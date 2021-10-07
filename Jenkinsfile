pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f java-tomcat-sample/pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Create Tomcat Docker image') {
            steps {
                sh 'docker build ./java-tomcat-docker -t tomcatsamplewebapp:${env.BUILD_ID}'
            }
        }
    }
}
