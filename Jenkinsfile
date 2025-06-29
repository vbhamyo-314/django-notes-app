 @Library("Shared") _
 pipeline {
    agent {label "vinod"}

    stages {
        stage ("Hello")
        {
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code") {
            steps {
                script{
                       clone("https://github.com/vbhamyo-314/django-notes-app.git","main")
                       echo "Cloning the code completed"
                }
            }
        }
        stage("Build") {
            steps {
                script {
                     docker_build("notes-app", "latest","vbhamyo")
                     echo "The Build completed"
                }
            }
        }
        stage("Test") {
            steps {
                echo "This is for testing the code"
            }
        }
        stage("Push to DockerHub") {
            steps {
                  script{
                      docker_push("notes-app","latest","vbhamyo")
                      echo "Pushing Image to DockerHub Completed"
                  }
                }
            }
         stage("Deploy") {
            steps {
                sh "docker compose up -d"
                echo "Deployment Completed"
            }
         }
        }
}
