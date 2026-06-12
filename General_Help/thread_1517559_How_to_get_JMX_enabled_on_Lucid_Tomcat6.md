---
title: "How to get JMX enabled on Lucid Tomcat6"
date: 2010-06-25
forum: General Help
---

### Post by yatesco on 2010-06-25
Hi,

I have Lucid with the tomcat6 package installed but I just cannot manage to connect to JMX over jconsole.

I have followed the following: [http://www.opennms.org/wiki/Tomcat_6_JMX_How-To](http://www.opennms.org/wiki/Tomcat_6_JMX_How-To) however it just doesn't appear in jconsole.

I followed the steps for allowing remote machines to connect, but again, no luck :(

Can anybody paste an idiot proof step by step guide on how you managed to enable JMX on Tomcat6 so it is accessible both locally and remotely.

Many thanks :)

Col

---

### Post by justleen on 2010-06-25
Can only show you the running startup options, but this works here:
 -server -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=1234 -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false

---

### Post by yatesco on 2010-06-25
> **justleen said:**
> Can only show you the running startup options, but this works here:
 -server -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=1234 -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false
Hi Justleen,

Yeah, I tried that but no luck :(  To make sure I wasn't go mad I downloaded a plan tomcat and installed it, made the above options and that works fine.

Oh well - thanks for trying :)

Col

---

