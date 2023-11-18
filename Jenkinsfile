pipeline {
    agent any
    
    stages{
        stage("Code"){
            steps{
                git url: "https://github.com/prajwal-github-devops/node-todo-cicd.git", branch: "master"
            }
        }
        stage("Build & Test"){
            steps{
                sh "docker build . -t node-app-test-new"
            }
        }
        stage("Push to DockerHub"){
            steps{
                withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"Sachin1998",usernameVariable:"praj1998")]){
                    sh "docker login -u ${env.praj1998} -p ${env.Sachin1998}"
                    sh "docker tag node-app-test-new ${env.praj1998}/node-app-test-new:latest"
                    sh "docker push ${env.praj1998}/node-app-test-new:latest" 
                }
            }
        }
        stage("Deploy"){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
