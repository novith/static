pipeline {
    agent any
    stages {
        stage('Lint HTML'){
            steps {
                tidy -q -e *.html
            }
        }        
        stage('Upload to AWS') {
            steps {
                withAWS(credentials: 'aws-static', region: 'us-west-1') {
                s3Upload(file:'index.html', bucket:'jenkins-project3')
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
                }
            }
        }
    }
}
