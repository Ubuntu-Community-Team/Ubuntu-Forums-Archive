---
title: "eclipse and tomcat 7"
date: 2011-09-22
forum: General Help
---

### Post by jdunn on 2011-09-22
I installed Helios Eclipse for JEE and Tomcat 7 per these OS independent instructions:  [http://www.coreservlets.com/Apache-Tomcat-Tutorial/tomcat-7-with-eclipse.html](http://www.coreservlets.com/Apache-Tomcat-Tutorial/tomcat-7-with-eclipse.html).  These instructions work fine for MS Windows but I'm having trouble on Ubuntu 11.04 64 bit.

I've added this line to .bashrc:  export JAVA_HOME=/usr/lib/jvm/java-6-sun

I can't get eclipse to start tomcat.  Any suggestions are appreciated.

---

### Post by jdunn on 2011-09-23
bump

---

### Post by Azdour on 2011-09-23
Hi,

I do not use Eclipse for JEE but I do use it with the Axis2 plugins and Tomcat. In my Eclipse under Window | Preferences, there is a Server listed and under that Runtime Environment. Here I see the Tomcat Server I defined. I can then click on Edit... and choose the JRE to use.

I do not have JAVA_HOME set so I think Eclipse in my case uses the JRE I define above.

Of course you may not have the Server Preferences but it may be something to check.

---

