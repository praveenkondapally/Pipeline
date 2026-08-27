node {

    stage('Checkout') {

        echo 'Checking out source code...'

        checkout scm
    }


    stage('Build') {

        echo 'Building Java application...'

        sh 'mvn clean compile'
    }


    stage('Test') {

        echo 'Running unit tests...'

        sh 'mvn test'
    }


    stage('Package') {

        echo 'Creating JAR package...'

        sh 'mvn package -DskipTests'

        echo 'Generated files:'

        sh 'ls -lh target/'
    }


    stage('Deploy') {

        echo 'Deploying application...'

        sh '''
            mkdir -p deployment

            cp target/java-maven-demo-1.0.jar deployment/

            echo "Application deployed successfully"

            ls -lh deployment/
        '''
    }


    stage('Application Test') {

        echo 'Testing deployed JAR...'

        sh '''
            java -jar deployment/java-maven-demo-1.0.jar
        '''
    }


    stage('Post Deployment') {

        echo '======================================'
        echo ' Jenkins Pipeline Completed Successfully '
        echo '======================================'
    }
}
