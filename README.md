# Spring MVC and Hibernate template application

This is a template for a web application that uses Spring MVC and Hibernate. The sample code is a simple CRUD page that manipulates records for a single model object. This
particular template has been modified from Heroku's Spring MVC and Hibernate template in the following manner:

 - Updated Spring to `4.0.6.RELEASE`.
 - Updated Hibernate Entity Manager to `4.3.6.Final`.
 - Added FasterXML's Jackson JSON processor.
 - Uses SLF4J for logging.
 - Uses Servlet 3.0 annotations for configuration (no `web.xml`).
 - Uses Spring annotations for application configuration (no `applicationContext.xml`).
 - Uses a patched version of Heroku's Web-Runner (patched to use Tomcat 7.0.54)
 - Uses Oracle's Java 8 (`1.8.0_05`) via a custom buildpack.

## Running the application locally

First build with:

    $ mvn clean install

Then run it with:

    $ java -jar target/dependency/webapp-runner.jar target/*.war
    
## Deploying the application to Heroku

Before you deploy to Heroku, you have to make sure that you set the `BUILDPACK_URL` URL to `http://github.com/vivin/heroku-buildpack-oracle-java`. This is a forked version
of [trautonen's buildpack](https://github.com/trautonen/heroku-buildpack-oracle-java) which has been modified to remove some options (no JCE or Ruby gems). You can set
`BUILDPACK_URL` under **Config Variables** in your Heroku app's settings, or you can set it from the command-line via:

    $ heroku config:set BUILDPACK_URL="http://github.com/vivin/heroku-buildpack-oracle-java"
    
After this you can deploy your app to Heroku and it will build using Oracle's JDK (initial deployment may take a little bit of time).



