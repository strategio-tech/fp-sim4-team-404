# [Cryptek](http://ec2-3-81-115-80.compute-1.amazonaws.com/) - Cryptocurrency monitoring made easy

<p>Cryptek is a web-app designed to facilitate an easily-navigable cryptocurrency monitoring hub. Users can view lists of cryptocurrency assets and associated details without too much visual clutter or overcomplication. Creating a suitable environment for cryptocurrency novices or those who want simple information without needless detail.</p>

![Front Page](Diagrams/Cryptek-front-page.png "Front Page")

## Features

- Allow user(s) to access a list of cryptocurrency assets (in order by price) — (based off the API)
- Allow user(s) to index the list of cryptocurrencies
- Allow user(s) to view details on a selected cryptocurrency
- Allow user(s) to view graphs / charts on a selected cryptocurrency
- Allow user(s) to favorite cryptocurrency assets to a ‘Watchlist’ through local storage
- Allow user(s) to unfavorite cryptocurrency assets
- Allow user(s) to access a web + mobile responsive app

## Architecture Diagram

![Architecture Diagram](Diagrams/Cryptek-Architecture-Diagram.png "Architecture Diagram")

## Local Installation

To run this project locally, the following must be installed:

- [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm#using-a-node-installer-to-install-node-js-and-npm) 8.5.1 or later
- [Node.js](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm#using-a-node-installer-to-install-node-js-and-npm) 16.14.0 or later

First, clone this repository, then go inside the directory:
```
  git clone https://github.com/strategio-tech/fp-sim4-team-404.git
  cd fp-sim4-team-404
```

Install the dependencies required:
```
  npm install --force
```

Finally, start the app:
```
  npm start
```



You can then navigate to `localhost:3000` to view the web app.

## Web Deployment

For the CI/CD pipeline and web deployment, a Github Action workflow is triggered whenever the following files or directories are modified:

- `public/`
- `src/`
- `package.json`
- `package-lock.json`
- `Dockerfile`

For the workflow to run smoothly, the user must do the following steps within an AWS account.
```
1) Create an ECR repository to store your images.
2) Create an ECS task definition, an ECS cluster, and an ECS service.
3) Store your ECS task definition as a JSON file in your GitHub repository.
4) Store an IAM user access key in GitHub Actions secrets named AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY.
```

The workflow file must then be modified with the proper variables to function properly. For more information, view the [aws.yml](.github/workflows/aws.yml) file.

Once the workflow is activated, the following steps occur automatically:
```
1) The workflow gains programmatic access to AWS services using AWS IAM credentials.
2) The workflow builds a Docker image for the app, then pushes this image to a public repository on AWS Elastic Container Registry (ECR).
3) The ID for the image in the ECR repository is added to an AWS Elastic Container Service (ECS) task definition.
4) The ECS task definition is deployed to an existing ECS cluster and service
```
This causes ECS to run the created task, which in turn deploys an EC2 instance that hosts the app.

As an example, the site can be accessed at http://ec2-3-81-115-80.compute-1.amazonaws.com/.

## References
App Story: https://docs.google.com/document/d/12ve871wYzzY7bPiGktWz_FFFPXAOvJ2jQBCUS0qPt6A/edit?usp=sharing

Toolchain: https://docs.google.com/document/d/173VKiQJNX3lcnYz6RxnbJpe36SKXekEk-vPCh3m6EFA/edit?usp=sharing
