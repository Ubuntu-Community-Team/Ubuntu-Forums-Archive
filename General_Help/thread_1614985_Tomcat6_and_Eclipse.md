---
title: "Tomcat6 and Eclipse"
date: 2010-11-06
forum: General Help
---

### Post by meastwood on 2010-11-06
I thought I'd post this as there seems to be a few issues with tomcat6 which I have just run into and very little response to them.

The main problem appears to be - see this blog
[http://opensourcecollection.blogspot.com/2010/08/how-to-install-tomcat6-sever-in-linux.html]("http://opensourcecollection.blogspot.com/2010/08/how-to-install-tomcat6-sever-in-linux.html")

I'm looking at Eclipse with ZK and ZK studio and using tomcat6 as the serverlet engine with lighttpd as a proxy.

I initially installed JAVA SDK, Eclipse and Tomcat6 via synaptic package manager using Ubuntu packages.

The java SDK seems okay though none of the environment variables were set or if they are they are implemented in some other fashion. 

Eclipse just wasn't right from the outset so I completely removed it and installed the binaries (from the project's website) in a location of my choosing and installed the ZK studio plugin via Eclipse. Pointed Eclipse to use the the java sdk's jre (/usr/lib/jvm/java-6-sun-1.6.0.22) instead of the generic gcj vm (which by the way is linked to jre version 1.5)

I then deployed the ZK zkdemo.war to tomcat6 - trying to access via the browser resulted in  'a java security, permissions error' which didn't make sense (to me).  Further investigations revealed that some files that were referenced in installation docs etc. just were not where they should be or where they were expected to be.
  
So .. completely removed tomcat6 and followed the advice in the blog (link above). I did not follow the instructions exactly - different locations and I've used /etc/profile  (single user development system) for setting my environment - relevant entries below

```
CATALINA_HOME="/usr/local/apache-tomcat-6.0.29"
ANT_HOME="/usr/local/apache-ant-1.8.1"
JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.22"
export JAVA_HOME CATALINA_HOME ANT_HOME
PATH="$ANT_HOME/bin:$JAVA_HOME/bin:$PATH"
```

Redeployed the .war file to the new install - displayed fine.

I have yet to start playing with Eclipse and ZK but now at least, on start up, there are no errors.  Whether all is well will be revealed when I try and build and deploy an app.!!

I also had trouble trying to build from source hence use of the appropriate binaries from the relevant websites.

In short - install manually using the project's tarballs  ...

---

