pipeline{
    agent{
        label 'webserver'
    }
    stages{
        stage('git checkout'){
            steps{
                git 'https://github.com/pavanparvathaneni/staticsite.git'
            }
        }
        stage('copying code'){
            steps{
                // sh "sudo cp -r /home/ec2-user/jenkins/workspace/UI-Build/* /var/www/html"
                sh "sudo cp -r ${WORKSPACE}/* /var/www/html"
                sh "cd /var/www/html ; ls -l;"
            }
        }
        stage('Restart apache'){
            steps{
                sh '''
                sudo systemctl restart httpd
                sudo systemctl status httpd
                date
                '''
            }
        }    
    }
    post {
    always {
          cleanWs()
          }
    }
}
