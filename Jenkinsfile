pipeline {
    agent any

    stages {
        stage('Preparation') {
            steps {
                echo 'Cloning the code from GitHub'
				sh'''
				rm -rf pythonexp
				git clone https://github.com/sairammagham/pythonexp.git
				'''
            }
        }
		
		stage('Docker Build') {
            steps {
                echo 'Building the Docker Image'
				sh'''
				
				cd pythonexp
				sudo docker build -t rams3/hello:2.0 .
				sudo docker images
				
				'''
            }
        }
		
		stage('Docker Deployment') {
            steps {
                echo 'docker run '
                sh '''
                sudo docker push rams3/hello:2.0
                sudo docker run -d -p 8089:3333 --name pythonapp rams3/hello:2.0
                sudo docker ps
                '''
            }
        }
    }
}