# Examples of HTML5 Applications for SAP Business Technology Platform Multi-Cloud Environments

[![REUSE status](https://api.reuse.software/badge/github.com/SAP-samples/multi-cloud-html5-apps-samples/)](https://api.reuse.software/info/github.com/SAP-samples/multi-cloud-html5-apps-samples/)

This repository contains examples of HTML5 applications for multiple SAP BTP environments. The examples show how you can use standalone application routers or managed application routers to achieve different goals and they demonstrate the capabilities of the SAP HTML5 Application Repository service for SAP BTP.

On the Cloud Foundry and Kyma environment of SAP BTP, you can run an application that was uploaded to the SAP HTML5 Application Repository service for SAP BTP using one of the following options: a standalone application router or a managed application router. Both options allow you to serve static content from the HTML5 Application Repository, authenticate users, rewrite URLs, and forward or proxy requests to other micro services while propagating user information. However, the option that is managed brings many benefits, such as:
- Simplifying and speeding up your development and deployment experience
- Saving resources by running a serverless HTML5 application, which doesn’t require any application runtime
- Lower maintenance efforts by leveraging the most up-to-date routing capabilities
- Meeting the changing demand for HTML5 applications by automatically adjusting the service to maintain consistent and predictable performance

In general, we recommend using the managed application router. Use an standalone application router preferably only in advanced cases, for example when application router extensibility is required.

For more information, see 
- [Developing HTML5 Applications with the Managed Application Router](https://help.sap.com/viewer/ad4b9f0b14b0458cad9bd27bf435637d/Cloud/en-US/c1b9d6facfc942e3bca664ae06387e9b.html)
- [Developing HTML5 Applications in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/11d77aa154f64c2e83cc9652a78bb985.html)

# Examples for SAP BTP, Cloud Foundry Environment

Before you start with the examples, please make sure that you are familiar with the basic concepts of HTML5 web apps in the Cloud Foundry environment, such as Cloud Foundry applications, services, service bindings. For more information, see [this video](https://www.youtube.com/watch?v=emnl-y9btdU).

The HTML5 Application Repository can hold any UI project independent of the used framework. Use the following commands of the [Cloud Foundry CLI plugin](https://sap.github.io/cf-html5-apps-repo-cli-plugin/) plugin to upload the HTML5 apps to the application repository:

```bash
mkdir myapp
cd myapp
echo '{"sap.app":{"id":"myapp","applicationVersion":{"version": "1.0.0"}}}' > manifest.json
echo '{"routes":[{"source":"^(.*)","target": "$1","service":"html5-apps-repo-rt"}]}' > xs-app.json
cf html5-push
```

For information about how to upload a react-based application to the HTML5 Application Repository, see [this blog post](https://blogs.sap.com/2019/06/03/cloudfoundryfun-5-play-asteroids-powered-by-react-secured-by-sap-cloud-platform/).

## Requirements
- You have an SAP BTP Trial account in the region Europe (Frankfurt). For creating the trial account, see this [tutorial](https://developers.sap.com/tutorials/hcp-create-trial-account.html).
- Node.js LTS version 14 is installed: <https://nodejs.org/en/download>
- Cloud Foundry Command Line tool (cf CLI)  is installed. For more information, see this [tutorial](https://developers.sap.com/tutorials/cp-cf-download-cli.html)
- The Multi-Target Application Cloud Foundry CLI [Plugin](https://github.com/cloudfoundry-incubator/multiapps-cli-plugin) (MultiApps CF CLI Plugin) is installed : 
    ```
    cf add-plugin-repo CF-Community https://plugins.cloudfoundry.org
    cf install-plugin multiapps
    ```
- GNU Make : <https://www.gnu.org/software/make>

    If you are running macOS or Linux it's likely that you already have Make installed. As a Windows user, please use the [Chocolatey](https://chocolatey.org/) package manager to install [Make](https://chocolatey.org/packages/make) via `choco install make`. After the installation, please check you can start the executable (`make`) from the terminal.


## HTML5 Apps Running on a Standalone Application Router

- [Basic app directly embedded into Cloud Foundry environment](standalone-approuter-html5-local-dir/)

- [Basic App stored on HTML5 Application Repository](standalone-approuter-html5-runtime)

- [Basic App stored on HTML5 Application Repository, using  XSUAA service, and destination service](standalone-approuter-html5-runtime-mta-hello-world)

- [Multi-tenant SAP Fiori app on HTML5 Application Repository](standalone-mtx-approuter)

- [SAP Fiori app integrated with SAP Cloud Portal service](standalone-portal-mta)

- [SAP Fiori app integrated with SAP Cloud Portal service and using UI5 flexibility service for key users](standalone-portal-keyuser-mta)


## HTML5 Apps Using the Managed Application Router

In contrast to the examples above, you don't need an application router for the following apps, which use the managed application router. This reduces the total cost of ownership (TCO) and you don't have to update the application router manually. 

- [Basic HTML5 App with a Managed Application Router, XSUAA service, and destination service](managed-html5-runtime-basic-mta)
- [SAP Fiori App with a Managed Application Router, XSUAA service, and destination service](managed-html5-runtime-fiori-mta)

### Optional backend service
- [SAP Fiori App example consume a public service, to use instead a CAP service with required authentication look at optional-self-hosted-backend](optional-self-hosted-backend)

# Examples for SAP BTP, Kubernetes Environment

## HTML5 Apps Using the Managed Application Router
- [Basic SAPUI5 App with a Managed Application Router and a Backend Component in the Kyma Runtime](managed-html5-runtime-jwt-kyma)

## Known Issues
None so far :)

## Support
This content is provided "as-is" with no other support.
