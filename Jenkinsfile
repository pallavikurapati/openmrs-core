pipeline {
    agent{label 'JDK11'}
    stages { 
        stage('source code') {
            steps {
                git branch : 'master', url:'https://github.com/pallavikurapati/openmrs-core.git'
            }
        }
        stage ('build the code') {
            steps {
                sh 'mvn compile'
            }
        }
        stage ('reporting') {
            steps {
                junit '**/surefire-report/*.xml'
            }
        }
        stage ('test results') {
            steps {
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
    }
}
