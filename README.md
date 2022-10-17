pipeline {
    agent any
   environment {
    name1= 'saif'
}



parameters {
    string(name: 'student', defaultValue: 'Saif', description: "Enter your name ")
    choice(name: 'address', choices: ['pune', 'abad', 'mumbai'], description: "")
    booleanParam(name: 'isStudent', defaultValue: true, description: "identify the ward")
}
    stages {
        stage('build') {
            steps {
                echo 'this is build stage '
                 sh 'echo "${name1}"'
                 sh 'echo "${student}"'
                 sh 'echo "${address}"'
                 sh 'echo "${isStudent}"'
                 
            }
    }
        stage('CQ') {
            input{
                    message "is code is riunning ? "
                    ok "yes its working "
                
                    }
             steps {
                    echo 'this is build stage '
                
             }
    }
        stage('Test') {
            steps {
                echo 'this is Test stage '
                sh 'echo "${name}"'
            }
    }
        stage('Deploy_SIT') {
            steps {
                echo 'this is deploy SIT stage '
            }
    }
        stage('build_UAT') {
            steps {
                echo 'this is Deploy to UAT stage '
            }
        }
    }
    }
