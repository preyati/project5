pipeline {
    agent any

    tools {
        nodejs 'NodeJS' // Ensnavigature this is configured in Jenkins → Global Tool Configuration
    }

    environment {
        ARTIFACT_NAME = 'app.zip'
        AZURE_WEBAPP_NAME = 'preyatiwebapp'
        AZURE_RESOURCE_GROUP = 'rg5-preyati'
    }

    stages {
        stage('Checkout from Git') {
            steps {
                git branch: 'main', url: 'https://github.com/preyati/project5.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Package App') {
            steps {
                sh 'zip -r $ARTIFACT_NAME .'
            }
        }

        stage('Publish Artifact') {
            steps {
                archiveArtifacts artifacts: "${ARTIFACT_NAME}", fingerprint: true
            }
        }

       
    }
}