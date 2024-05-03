pipeline {
    agent { 
        label "agentfarm"
    }
    stages {
        stage('Build') {
            steps {
                sh 'chmod +x build.sh'
                sh 'bash build.sh'
            }
        }
   stage('Test') {
            steps {
                sh 'chmod +x start.sh'
                sh 'bash start.sh'
            }
        }
   stage('Creating_artifacts') {
            steps {
                sh 'chmod +x artifact.sh'
                sh 'bash artifact.sh'
            }
        }


    }
   post {
        always {
            archiveArtifacts artifacts: '/opt/jenkins/workspace/python-pipeline123/dist/**/*.tar.gz', fingerprint: true
            junit 'build/reports/**/*.xml'
        }
    }
}

