pipeline {
    agent any
    stages{
        stage('git cloned'){
            steps{
                git url:'https://github.com/rajeev023/Project-B-F-/, branch: "master"'
              
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t rajeev20/projectfinance:v1 .'
                    sh 'docker images'
                }
            }
        }
          stage('Docker login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-pwd', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                    sh "echo $PASS | docker login -u $USER --password-stdin"
                    sh 'docker push rajeev20/projectfinance:v1'
            
        }
          } 
     stage('Deploy') {
            steps {
               script {
                   sh   'sudo docker run -itd --name My-first-containe2211 -p 8083:80 rajeev20/projectfinance:v1'
                }
            }
        }
    }
 }
