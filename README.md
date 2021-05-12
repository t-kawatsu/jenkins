# jenkins server

https://www.jenkins.io/doc/book/


## Prerequisites

- Docker engine


## Install

```
$ docker-compose build
$ docker-compose run -d
```


## Post-installation setup

https://www.jenkins.io/doc/book/installing/docker/#setup-wizard


## Examples

### Jenkinsfile - SCM/Docker

```
pipeline {
    agent {
        dockerfile {
            filename 'Dockerfile'
            dir '.'
            additionalBuildArgs  '--no-cache --network host'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'make build'
            }
        }
        stage('Test') {
            steps {
                sh 'make test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'make deploy'
            }
        }
    }
}

```
