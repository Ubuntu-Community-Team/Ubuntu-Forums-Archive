---
title: "Install J2EE in Ubuntu"
date: 2009-08-31
forum: General Help
---

### Post by Elv13 on 2009-08-31
Does anybody manager to install J2EE in Ubuntu 9.04 32bit? The (.bin) installer from SUN on my computer crash. Can someone provide a working way to install it or a .deb?

I can't find anyone in Linux with this thing working...

(And yes, I need EE, not SE)

---

### Post by Mighty_Joe on 2009-09-01
> **Elv13 said:**
> 
(And yes, I need EE, not SE)

Exactly what are you trying to install?  J2EE is a specification.  It is implemented by various vendors (i.e. IBM has Websphere, Oracle has Weblogic, Sun has Glassfish).  If you got it from Sun, it's probably [Glassfish]("http://java.sun.com/javaee/downloads/index.jsp?userOsIndex=6&userOsId=windows&userOsName=Windows").  I just want to make sure we're looking at the same thing.

---

### Post by Elv13 on 2009-09-01
I need sun j2ee (Glassfish) to do some JSP on a tomcat server and use Eclipse

---

### Post by Mighty_Joe on 2009-09-01
I downloaded Glassfish 2.1 from [here]("https://glassfish.dev.java.net/downloads/v2.1-b60e.html") (the 54Mb JAR file under the Linux Platform header) and followed the "Instructions to unbundle and configure GlassFish" on the same page:
```

export JAVA_HOME=/usr/lib/jvm/java-6-sun=1.6.0.14
java -Xmx256m -jar glassfish-installer-v2.1-b60e-linux.jar
chmod -R +x lib/ant/bin
lib/ant/bin/ant -f setup.xml

```

I can see the Glassfish start page in a browser after I do the [quick start]("http://docs.sun.com/app/docs/doc/820-4334/aboaa?a=view").

---

