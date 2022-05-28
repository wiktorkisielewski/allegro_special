# CI pipeline for .NET WebAPI services

This repository contains:
- 3 WebAPI Services in .NET Core (3.1)
- XUnit tests for every Service
- CI pipeline (for Azure)

## WebApi Services & XUnit tests

These are simple Web API services made in .NET CORE 3.1, each of them has an XUnit test.
They serve a basic functionality - returning Weather Forcast

### Services:

- [Service1](Service1/Wiktor.Kisielewski.Service1/)

- [Service2](Service2/Wiktor.Kisielewski.Service2/)

- [Service3](Service3/Wiktor.Kisielewski.Service3/)

[Microsoft Docs](https://docs.microsoft.com/en-us/aspnet/core/tutorials/first-web-api?view=aspnetcore-6.0&viewFallbackFrom=as&tabs=visual-studio)

### Tests:

- [Test for Service1](Service1/Wiktor.Kisielewski.Service1.Tests/)

- [Test for Service2](Service2/Wiktor.Kisielewski.Service2.Tests/)

- [Test for Service3](Service3/Wiktor.Kisielewski.Service3.Tests/)

> The XUinit test are not really testing anything, their outcome is always positive. They are used as a part of a CI process.

## CI pipeline

This repository is integrated with a Continuous Integration pipeline hosted on [Azure DevOps](https://azure.microsoft.com/en-us/services/devops/)

> [`CI/azure-pipelines.yml`](CI/azure-pipelines.yml)

### Pipeline steps:

PR (pull request) to the `master` branch is created

**&#8595;**

The pipeline is **automatically** triggered by the above action

**&#8595;**

The WebAPI service is run and tested by the XUnit test

[This is repeated 3 times - one execution for every service]

**&#8595;**

Every service is containerized (as a docker image) with a `Dockerfile` (example file for [Service1](Service1/Wiktor.Kisielewski.Service1/Dockerfile))

**&#8595;**

Docker images are tagged and pushed to docker registry -[hub.docker.com](https://hub.docker.com/repository/docker/wiktorkisielewski/allegro_special/general)

**&#8595;**

The PR is ready to be merged