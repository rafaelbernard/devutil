# bitbuckets pipelines

Some simple examples for bitbuket pipelines

# php, test and deploy via ssh

Testing the application and, if success, deploy the entire repository acessing the server via ssh.

The deploy ste will run just at master branch.

```yml
# This is a sample build configuration for PHP.
# Check our guides at https://confluence.atlassian.com/x/e8YWN for more examples.
# Only use spaces to indent your .yml configuration.
# -----
# You can specify a custom docker image from Docker Hub as your build environment.
image: php:7.1-alpine

pipelines:
  default:
    - step:
        script:
          - apt-get update && apt-get install -y unzip
          - curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
          - composer install
  branches:
    master:
      - step:
          script:
            - apt-get update && apt-get install -y ssh
            - ssh user@example.com "cd /var/www && git pull"

```
