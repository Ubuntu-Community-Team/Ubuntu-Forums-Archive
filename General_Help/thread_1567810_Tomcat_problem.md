---
title: "Tomcat problem"
date: 2010-09-04
forum: General Help
---

### Post by _sluimers_ on 2010-09-04
Hello there, my server crashed, so I had to reinstall everything again.

It's been a long time since I've looked at how I've managed to get tomcat working and all and right now I maybe have tomcat running, but nothing is been deployed. Not my war file nor the examples, docs and manager.
I don't have a clue as to why.

Here's my server.xml:

```

<?xml version='1.0' encoding='utf-8'?>
<!--
  Licensed to the Apache Software Foundation (ASF) under one or more
  contributor license agreements.  See the NOTICE file distributed with
  this work for additional information regarding copyright ownership.
  The ASF licenses this file to You under the Apache License, Version 2.0
  (the "License"); you may not use this file except in compliance with
  the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License.
-->
<!-- Note:  A "Server" is not itself a "Container", so you may not
     define subcomponents such as "Valves" at this level.
     Documentation at /docs/config/server.html
 -->
<Server port="8005" shutdown="SHUTDOWN">

  <!--APR library loader. Documentation at /docs/apr.html -->
  <!--
  <Listener className="org.apache.catalina.core.AprLifecycleListener" SSLEngine="on" />
  -->
  <!--Initialize Jasper prior to webapps are loaded. Documentation at /docs/jasper-howto.html -->
  <Listener className="org.apache.catalina.core.JasperListener" />
  <!-- Prevent memory leaks due to use of particular java/javax APIs-->
  <Listener className="org.apache.catalina.core.JreMemoryLeakPreventionListener" />
  <!-- JMX Support for the Tomcat server. Documentation at /docs/non-existent.html -->
  <Listener className="org.apache.catalina.mbeans.ServerLifecycleListener" />
  <Listener className="org.apache.catalina.mbeans.GlobalResourcesLifecycleListener" />

  <!-- Global JNDI resources
       Documentation at /docs/jndi-resources-howto.html
  -->
  <GlobalNamingResources>
    <!-- Editable user database that can also be used by
         UserDatabaseRealm to authenticate users
    -->
    <Resource name="UserDatabase" auth="Container"
              type="org.apache.catalina.UserDatabase"
              description="User database that can be updated and saved"
              factory="org.apache.catalina.users.MemoryUserDatabaseFactory"
              pathname="conf/tomcat-users.xml" />
  </GlobalNamingResources>

  <!-- A "Service" is a collection of one or more "Connectors" that share
       a single "Container" Note:  A "Service" is not itself a "Container", 
       so you may not define subcomponents such as "Valves" at this level.
       Documentation at /docs/config/service.html
   -->
  <Service name="Catalina">
  
    <!--The connectors can use a shared executor, you can define one or more named thread pools-->
    <!--
    <Executor name="tomcatThreadPool" namePrefix="catalina-exec-" 
        maxThreads="150" minSpareThreads="4"/>
    -->
    
    
    <!-- A "Connector" represents an endpoint by which requests are received
         and responses are returned. Documentation at :
         Java HTTP Connector: /docs/config/http.html (blocking & non-blocking)
         Java AJP  Connector: /docs/config/ajp.html
         APR (HTTP/AJP) Connector: /docs/apr.html
         Define a non-SSL HTTP/1.1 Connector on port 8080
    -->
    <Connector port="8888" protocol="HTTP/1.1" 
               connectionTimeout="20000" 
               URIEncoding="UTF-8"
               redirectPort="8443" />
    <!-- A "Connector" using the shared thread pool-->
    <!--
    <Connector executor="tomcatThreadPool"
               port="8080" protocol="HTTP/1.1" 
               connectionTimeout="20000" 
               redirectPort="8443" />
    -->           
    <!-- Define a SSL HTTP/1.1 Connector on port 8443
         This connector uses the JSSE configuration, when using APR, the 
         connector should be using the OpenSSL style configuration
         described in the APR documentation -->
    <!--
    <Connector port="8443" protocol="HTTP/1.1" SSLEnabled="true"
               maxThreads="150" scheme="https" secure="true"
               clientAuth="false" sslProtocol="TLS" />
    -->

    <!-- Define an AJP 1.3 Connector on port 8009 -->
    <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />


    <!-- An Engine represents the entry point (within Catalina) that processes
         every request.  The Engine implementation for Tomcat stand alone
         analyzes the HTTP headers included with the request, and passes them
         on to the appropriate Host (virtual host).
         Documentation at /docs/config/engine.html -->

    <!-- You should set jvmRoute to support load-balancing via AJP ie :
    <Engine name="Catalina" defaultHost="localhost" jvmRoute="jvm1">         
    --> 
    <Engine name="Catalina" defaultHost="localhost">

      <!--For clustering, please take a look at documentation at:
          /docs/cluster-howto.html  (simple how to)
          /docs/config/cluster.html (reference documentation) -->
      <!--
      <Cluster className="org.apache.catalina.ha.tcp.SimpleTcpCluster"/>
      -->        

      <!-- The request dumper valve dumps useful debugging information about
           the request and response data received and sent by Tomcat.
           Documentation at: /docs/config/valve.html -->
      <!--
      <Valve className="org.apache.catalina.valves.RequestDumperValve"/>
      -->

      <!-- This Realm uses the UserDatabase configured in the global JNDI
           resources under the key "UserDatabase".  Any edits
           that are performed against this UserDatabase are immediately
           available for use by the Realm.  -->
      <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
             resourceName="UserDatabase"/>

      <!-- Define the default virtual host
           Note: XML Schema validation will not work with Xerces 2.2.
       -->
      <Host name="localhost"  appBase="webapps"
            unpackWARs="true" autoDeploy="true"
            xmlValidation="false" xmlNamespaceAware="false">

        <!-- SingleSignOn valve, share authentication between web applications
             Documentation at: /docs/config/valve.html -->
        <!--
        <Valve className="org.apache.catalina.authenticator.SingleSignOn" />
        -->

        <!-- Access log processes all example.
             Documentation at: /docs/config/valve.html -->
        <!--
        <Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"  
               prefix="localhost_access_log." suffix=".txt" pattern="common" resolveHosts="false"/>
        -->

      </Host>
    </Engine>
  </Service>
</Server>

```

Here's my are my log files:
/var/log/apache2.error.log
```

[Sun Sep 05 19:56:19 2010] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Sun Sep 05 19:56:20 2010] [notice] Apache/2.2.14 (Ubuntu) mod_fcgid/2.3.4 PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch mod_ssl/2.2.14 OpenSSL/0.9.8k configured -- resuming normal operations
[Sun Sep 05 21:00:57 2010] [error] [client 82.171.16.94] File does not exist: /var/www/favicon.ico

```

/var/log/catalina.2010-09-05.log
```

Sep 5, 2010 12:09:26 PM org.apache.catalina.core.AprLifecycleListener init
INFO: The APR based Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server:/usr/lib/jvm/java-6-openjdk/jre/lib/amd64:/usr/lib/jvm/java-6-openjdk/jre/../lib/amd64:/usr/java/packages/lib/amd64:/usr/lib/jni:/lib:/usr/lib
Sep 5, 2010 12:09:26 PM org.apache.coyote.http11.Http11Protocol init
INFO: Initializing Coyote HTTP/1.1 on http-8888
Sep 5, 2010 12:09:26 PM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 2078 ms
Sep 5, 2010 12:09:26 PM org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
Sep 5, 2010 12:09:26 PM org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/6.0.24
Sep 5, 2010 12:09:27 PM org.apache.catalina.startup.HostConfig deployDescriptor
INFO: Deploying configuration descriptor ROOT.xml
Sep 5, 2010 12:09:27 PM org.apache.catalina.startup.HostConfig deployDescriptor
INFO: Deploying configuration descriptor docs.xml
Sep 5, 2010 12:09:27 PM org.apache.catalina.startup.HostConfig deployDescriptor
INFO: Deploying configuration descriptor host-manager.xml
Sep 5, 2010 12:09:27 PM org.apache.catalina.startup.HostConfig deployDescriptor
INFO: Deploying configuration descriptor examples.xml
Sep 5, 2010 12:09:28 PM org.apache.catalina.startup.HostConfig deployDescriptor
INFO: Deploying configuration descriptor manager.xml
Sep 5, 2010 12:09:28 PM org.apache.coyote.http11.Http11Protocol start
INFO: Starting Coyote HTTP/1.1 on http-8888
Sep 5, 2010 12:09:29 PM org.apache.jk.common.ChannelSocket init
INFO: JK: ajp13 listening on /0.0.0.0:8009
Sep 5, 2010 12:09:29 PM org.apache.jk.server.JkMain start
INFO: Jk running ID=0 time=0/33  config=null
Sep 5, 2010 12:09:29 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 2180 ms

```

---

### Post by _sluimers_ on 2010-09-18
bump

---

### Post by _sluimers_ on 2010-09-23
bump

---

### Post by _sluimers_ on 2010-09-30
bump

---

### Post by _sluimers_ on 2010-10-03
bump

---

### Post by _sluimers_ on 2010-10-03
Okay, I found out why my examples and manager isn't working because I forgot I turned them off looking at [http://ubuntuforums.org/showthread.php?t=1149507](http://ubuntuforums.org/showthread.php?t=1149507)
and see I took away the lines where Tomcat's manager and examples are allowed. This still leaves me without a deployed war file, anyone has an idea why they're not being deployed?

[EDIT] I'll make a new thread for this as the question has altered.[/EDIT]

---

