[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

<p align="center"><img src="https://raw.githubusercontent.com/sirixdb/sirix/master/logo.png"/></p>

[![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?text=SirixDB+-+a+storage+system%2C+which+creates+%28very+small-sized%29+snapshots+of+your+data+on+every+transaction-commit+through+the+implementation+of+a+novel+sliding+snapshot+algorithm.&url=http://sirix.io&via=sirix&hashtags=versioning,diffing,xml,kotlin,coroutines,vertx)

[![Follow](https://img.shields.io/twitter/follow/sirixdb.svg?style=social)](https://twitter.com/sirixdb)

[Join us on Slack](https://join.slack.com/t/sirixdb/shared_invite/enQtNjI1Mzg4NTY4ODUzLTE3NmRhMWRiNWEzMjQ0NjAxNTZlODBhMTQzMWM2Nzc5MThkMjlmMzI0ODRlNGE0ZDgxNDcyODhlZDRhYjM2N2U) | [Community Forum](https://sirix.discourse.group/)

**Working on your first Pull Request?** You can learn how from this *free* series [How to Contribute to an Open Source Project on GitHub](https://egghead.io/series/how-to-contribute-to-an-open-source-project-on-github)

<h1 align="center">SirixDB Web frontend - An Evolutionary, Versioned, Temporal NoSQL Document Store</h1>
<h2 align="center">Store and query revisions of your data efficiently</h2>

>"Remember that you're lucky, even if you don't think you are, because there's always something that you can be thankful for." - Esther Grace Earl (http://tswgo.org)

## Introduction

**Discuss it in the [Community Forum](https://sirix.discourse.group)**

This is the repository for a web frontend based on [Vue.js](https://vuejs.org), [D3.js](https://d3js.org) and [TypeScript](https://www.typescriptlang.org).

It'll provide several interaction possibilities to store, update and query databases in SirixDB. Furthermore the front-end will provide interactive visualizations for exploring and comparing revisions of resources stored in SirixDB based on different views.

**Some ideas for comparing revisions of the XML or JSON resources, which need to be ported from a Java GUI/Processing can be found in my [Master's Theses](
https://github.com/JohannesLichtenberger/master-thesis/blob/master/Master/Thesis/thesis.pdf) and in a [Screencast](http://www.youtube.com/watch?v=l9CXXBkl5vI).**

## Test and edit in Gitpod
[![Edit and test in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/sirixdb/sirix-web-frontend)

Test and edit this project in a web based VS code environment.
## Project setup
**We currently face the following [issue](https://github.com/sirixdb/sirix-web-frontend/issues/18), whereas this [workaround](https://github.com/nuxt/typescript/issues/49#issuecomment-531086770) works until Nuxt.js or Element-UI fix the issue**

We've created a `Dockerfile` and a `docker-compose.yml` file to simplify the setup process. However you still have to setup Keycloak as desribed in the documentation for the REST-API (especially assigning the roles to an admin-user):

In order to use the `docker-compose`:

1. `mkdir sirixdb`
2. `git clone https://github.com/sirixdb/sirix.git`
3. `git clone https://github.com/sirixdb/sirix-web-frontend.git`
4. Copy the `docker-compose.yml` file from `sirix-web-frontend` to your `sirixdb` parent folder.
5. Start Keyclock with the command `sudo docker-compose up waitforkeycloak` from your sirixdb directory with the copied `docker-compose.yml` file.
6. In your browser navigate to http://127.0.0.1:8080 and click on the link "Administration Console".
7. Use username "admin", password "admin" to log in.
8. Navigate to `Clients` => `sirix`.
9. Set `Standard Flow Enabled`.
10. Set redirect URL to `http://localhost:3005/callback`.
11. Navigate to the `Credentials` tab and generate a new secret.
12. Put this secret in `sirix/bundles/sirix-rest-api/src/main/resources/sirix-conf.json` as the value for `client.secret`.
13. Start the SirixDB HTTP-Server: `sudo docker-compose up -d server`
13. Start the Node.js Server: `sudo docker-compose up -d frontend`
14. In your browser call http://127.0.0.1:3005 and the frontend should appear.

Without Docker for setting up the web frontend:

``` bash
# install dependencies
$ npm run install

# serve with hot reload at localhost:3005
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

### Customize configuration
For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).
