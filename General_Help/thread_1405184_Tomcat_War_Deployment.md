---
title: "Tomcat War Deployment"
date: 2010-02-12
forum: General Help
---

### Post by ewhitmor on 2010-02-12
Hello all, 

I am using apache2, tomcat6, ubuntu server 9.10 and GWT 2.0.  After about 60 hours of non stop trying i have finally configured everything so "stuff" happens without errors.

My question is this:

Can you deploy an exploded context directly to the webapps directory or do you have to use a WAR file and use the tomcat deployment web interface to deploy?  

I have been searching for days and cant seem to get my webapp to work unless i deploy a war file which i dont want to do due to complications in the development process.  Any help from a tomcat guru would be appreciated.

---

### Post by ewhitmor on 2010-02-12
Here is my situation in its entirety:

[LIST=1]
[*]Installed Ubuntu Server 9.10
[*]Installed Apache 2
[*]Installed Tomcat 6
[*]Installed libapache2-mod-jk
[*]Configured workers.properties
[*]configured apache
[*]configured tomcat
[/LIST]

At this point i was able to get virtual hosting working so that apache would accept the request, pass to mod_jk, which then passed to tomcat.

I updated my tomcat 6 server.xml file to the following:
```
<?xml version='1.0' encoding='utf-8'?>


<Server port="8005" shutdown="SHUTDOWN">

  <Listener className="org.apache.catalina.core.JasperListener" />
  <Listener className="org.apache.catalina.mbeans.ServerLifecycleListener" />
  <Listener className="org.apache.catalina.mbeans.GlobalResourcesLifecycleListener" />

  <GlobalNamingResources>

    <Resource name="UserDatabase" auth="Container"
              type="org.apache.catalina.UserDatabase"
              description="User database that can be updated and saved"
              factory="org.apache.catalina.users.MemoryUserDatabaseFactory"
              pathname="conf/tomcat-users.xml" />
  </GlobalNamingResources>

  <Service name="Catalina">
    <Connector port="8080" protocol="HTTP/1.1" connectionTimeout="20000" redirectPort="8443" />
	<Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />

    <Engine name="Catalina" defaultHost="localhost">
		<Realm className="org.apache.catalina.realm.UserDatabaseRealm" resourceName="UserDatabase"/>
		<!-- Define the default virtual host -->
		<Host name="localhost" 		appBase="webapps" 	unpackWARs="true" autoDeploy="true" xmlValidation="false" xmlNamespaceAware="false" />
		<Host name="test.domain1.org"  	appBase="domain1" 	unpackWARs="true" autoDeploy="true" xmlValidation="false" xmlNamespaceAware="false" >
			<Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs" prefix="domain1_access_log." suffix=".txt" pattern="common" resolveHosts="false"/>
  		</Host>
		<Host name="test.domain2.org"  	appBase="domain2" 	unpackWARs="true" autoDeploy="true" xmlValidation="false" xmlNamespaceAware="false" >
			<Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs" prefix="access_log2." suffix=".txt" pattern="common" resolveHosts="false"/>
        	</Host>
    </Engine>
  </Service>
</Server>
```

and put an exploded context into the test.domain1.org folder.  

When i navigate my browser to the domain i can see my webpage with my client side content being displayed.  But as soon as i need to make a server side call i get a 404 error.

it appears that the servlet mapping is not working so i checked the web.xml file in the root context directory.  It looks correct:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE web-app
    PUBLIC "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
    "http://java.sun.com/dtd/web-app_2_3.dtd">

<web-app>
  
  <!-- Servlets -->
  <servlet>
    <servlet-name>loginServlet</servlet-name>
    <servlet-class>tmst.vtd2.server.serviceImpl.LoginServiceImpl</servlet-class>
  </servlet>
  
  <servlet>
    <servlet-name>createUserServlet</servlet-name>
    <servlet-class>tmst.vtd2.server.serviceImpl.CreateUserServiceImpl</servlet-class>
  </servlet>  
  
  <servlet-mapping>
    <servlet-name>loginServlet</servlet-name>
    <url-pattern>/vtd2/login</url-pattern>
  </servlet-mapping>
  
  <servlet-mapping>
    <servlet-name>createUserServlet</servlet-name>
    <url-pattern>/vtd2/createUser</url-pattern>
  </servlet-mapping>  
  
  <!-- Default page to serve -->
  <welcome-file-list>
    <welcome-file>VTD2.html</welcome-file>
  </welcome-file-list>

</web-app>

```

/var/lib/tomcat6/conf/Catalina/test.domain1.org/ROOT.xml looks like this:
```

<?xml version='1.0' encoding='utf-8'?>
<Context displayName="test.domain1.org" docBase="" path="/" antiResourceLocking="false" >
</Context>



```

Yet my log still says:
```
192.168.1.50 - - [12/Feb/2010:10:58:15 -0500] "POST /vtd2/createUser HTTP/1.1" 404 1000
```

---

### Post by ewhitmor on 2010-02-12
Update:
If i use a WAR file which hasnt been exploded and use the tomcat webapp manager to deploy it the website starts working.  The difference between deploying the context and just copying the exploded context code into the directory is that eclipse is putting all the exploded class code into a JAR file instead of putting them directly into the file structure.

So back to my original question:  What does deployment in tomcat do when it deploys the war files?

---

### Post by ewhitmor on 2010-02-15
I figured it out.  Tomcat 6 has the invoker servlet disabled by default.  I guess you need this in order to run gwt 2.0 with an exploded webapp.  There are security issues according to the tomcat documentation that i am looking into but this at least got my app running.  Here is what i did:

/var/lib/tomcat6/conf/web.xml
uncomment the following code
```

    <servlet>
        <servlet-name>invoker</servlet-name>
        <servlet-class>
          org.apache.catalina.servlets.InvokerServlet
        </servlet-class>
        <init-param>
            <param-name>debug</param-name>
            <param-value>0</param-value>
        </init-param>
        <load-on-startup>2</load-on-startup>
    </servlet>

```

and in your v.host ROOT.xml file set the website to privileged
```

<?xml version='1.0' encoding='utf-8'?>
<Context displayName="test.domain2.org" docBase="/var/lib/tomcat6/webapps/domain2/" path="/mywebapp" antiResourceLocking="false" **privileged="true"**>
</Context>

```

I hope this helps someone else because i spend weeks working on it.

---

