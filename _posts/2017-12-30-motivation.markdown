---
layout: post
title: "Motivation"
category: misc
date: "2017-12-30 21:00:28 +0100"
author: richard.attermeyer
---
Just kicking of the new open delivery project at the end of the year.
I've been working ont this project for some time in my spare time.
Before I changed position in my company during summer, I was very much
involved in building continuous delivery platforms for different customers.
The last one involved the automation of deployment of the Atlassian stack into
an Amazon AWS VPC and developing a provisioning app.
This provisioning app allows to create the required resources
(Confluence spaces, Jira Project, Bitbucket projects and repositories
and OpenShift projects and resources), so you a developer can clone
a quickstarter project, make some modifications, commit and push it and
have access from the internet within 5 minutes.
So the provisioning app development also included development of template / quickstarter
projects for the defined stack (Angular frontend, Node.JS Backend, Spring Boot Backend, rstudio).
Openshift was not directly part of the game, because it was provided as a Red Hat managed service.

Before that, I was working on getting 24 developers on a docker based self-hosted
continuous delivery cluster. We started before the docker hype really was starting off
and decided to roll our own solution first, then Docker Swarm and Overlay
and integrate Log Management and monitoring to the stack and everything else
required. Initially based continuous delivery on Jenkins 1 and mirgrated to Jenkins 2.
In this scenario, we had long running projects and some infrastructure, like
Gitlab, Atlassian (Confluence, Jira), that was hosted centrally by different teams.
But our stack and the work we performed lead administrators to request that
new projects must deliver docker images and a property file to get deployed from 2018.

Until this summer, I had my hands on the infrastructure for 3 days / week.
The other 2 days were already filled with what some people would call management.
This has shifted. I am now in a management position. Probably having a chance (among other things),
to push forward a project, similar to the one described above, based on OpenShift.
But the first 6 months also involved consulting a client to migrate from
a Java monolith to a more distributed system architecture ("microservices architecture").

This client has "bought" a cloud foundry platform. I am curious how this will work for them.
The platform is managed by a "platform team", located in a different city, not sitting along with the
team that has the need for the first real business application on the platform, ...
Not an ideal solution.

In my opinion, it is crucial, that development teams (I am talking of dev team of around 20-50 developers),
develop the capability to manage such a platform on their own.
I am also convinced, that there will not be a single platform to address the needs
of all stakeholders and use cases (development, production, developers, operations).
So, I build this project, to consolidate my learings over the last 5 years and
have a place to experiment with new technologies.

So it is not directly meant to be used in production settings, and the continuous delivery platform
for your developers is also a production environment (for your developers).
You first need to understand the needs and processes around delivering software
for your company, team or project.

So, currently, I try to develop the documentation and push the technological
base forward.
Currently, most basic components of the "runtime environmet" (more on the domains later in the documentation, or (in German) on the [cattlecrew blog](https://thecattlecrew.net/2017/11/16/das-ganze-ist-mehr-als-seine-teile/)).

What is currently deployed

* consul (service discovery, K/V store)
* vault (secrets management)
* docker (containers)
* docker registry
* nomad (cluster scheduler)
* graylog (log management)
  - elasticsearch
  - mongodb
  - collectors (graylog)
* prometheus / grafana
  - cadvisor
  - node_exporter
* a pki (creating TLS certificates)

But a lot of features are missing

* Graylog should be configured correctly automatically, so  it directly can receive logs
* Clean up of documentation (left-overs from other projects)
* Basic grafana dashboards, to observe
  - cluster health
  - host metrics
  - application monitoring
* Gitlab and gitlab-ci
  - Code Hosting
  - build pipeline
* More elaborated registry frontend (portus, VMWare Harbor, ...) incl. Docker image scanning
* Nexus (NPM, Maven repository / proxy)
* Sonarqube
* using vault to create certificates, where it makes sense
* having an ansible module ready to interact with nomad
* LDAP (as user database)
* JBoss Keycloak (as IAM and oauth provider)
* Integration of various applications with oauth server or LDAP
* fabio as frontend load balancer
* LB for internal load balancing (e.g. from hosts to graylog)
* think about an SDN solution (contiv)
* sample projects
* and many more
* Migrate to "standard" ansible roles, where appropriate

So, any help welcome.
