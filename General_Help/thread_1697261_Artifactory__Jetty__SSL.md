---
title: "Artifactory / Jetty / SSL"
date: 2011-02-28
forum: General Help
---

### Post by jon.mithe on 2011-02-28
Hi,

Rapidly getting stuck, wandering if anyone can help point me in the right direction.

Trying to install Artifactory and accessing via HTTPS.  I can get it installed over HTTP but not HTTPS.

First off, I installed jetty, set the SSL connectors and mostly seemed working (I could access via https).  Then I had trouble redirecting through apache.  So I uninstalled it, and gave tomcat6 a blast.  

That turned out to be a very painfuil experience as my site would never load, and always seemed driven to listen on 8081 even though I set 8089 in the servers.xml.

Anyway, given up on tomcat and reinstalled the jetty. (unpack artifactory and rant the ./install.sh / jetty one (after clearing out all the /etc srtifactory stuff)).

Now it works over HTTP if I want it to but fails miserably over HTTPS.  

Looking at the coonsoleout.log I see the following error:

```
java.lang.ClassNotFoundException: org.mortbay.jetty.security.SslSocketConnector
Could not start the Jetty server: java.lang.ClassNotFoundException: org.mortbay.jetty.security.SslSocketConnector
java.lang.ClassNotFoundException: org.mortbay.jetty.security.SslSocketConnector
	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)

```

I know what the error means, but strugelling to see why its hapenning as I have set it up like before (albeit I lost the original ssl config).

Its weird, as this connector should exist.  Think it may be something with the classpath, but its set up the same before / it can work on http fine.

Stuck and have the feeling the last 4 hours of my life have been a complete waste :/

This is my jetty.xml connector definition :

```

 <Call name="addConnector">
     <Arg>
        <New class="org.mortbay.jetty.security.SslSocketConnector">
        <Set name="Port">8081</Set>
        <Set name="maxIdleTime">30000</Set>
        <Set name="keystore">/etc/keystore/proper.keystore</Set>
        <Set name="password">password</Set>
        <Set name="keyPassword">password</Set>
      </New>
    </Arg>
  </Call>

```

Anyone have and suggestions?

Thanks for any help,
Jon

---

### Post by jon.mithe on 2011-02-28
sigh, after sniffing around the library jars for jetty it turns out the correct answer was:

```
<New class="org.eclipse.jetty.server.ssl.SslSocketConnector">
```

brilliant when things are documented correctly, makes life so much easier :/

---

