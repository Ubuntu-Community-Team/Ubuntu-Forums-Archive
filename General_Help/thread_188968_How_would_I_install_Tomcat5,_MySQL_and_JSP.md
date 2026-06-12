---
title: "How would I install Tomcat5, MySQL and JSP?"
date: 2006-06-04
forum: General Help
---

### Post by FireFusion on 2006-06-04
I need them for a university project. I'm a bit of a beginner so go easy.

---

### Post by mlind on 2006-06-04
Use apt-get or **synaptic** to install Sun's java (you need JDK), tomcat 5 and mysql. Tomcat
contains JSP compiler called Jasper, so you don't have to anything to get JSP
support. Use synaptic for easier installation. Search forums if you don't know how.
You'll find the package names by searching on synaptic.


After installing Sun's java, use
*sudo update-alternavites --config java* and choose Sun's java. You may have to do same thing for javac.

Tomcat needs JAVA_HOME environment variable to be defined, put this on */etc/environment*.
It should point to the JDK path.

There's docs available for mysql, tomcat and JSP development on their respective sites.

---

### Post by FireFusion on 2006-06-05
Thanks. I think I managed to install everything but being a newb to this sort of thing I don't know what to do next or how to access anything. Could you point me in the right direction of a full guide of something?

Thank you.

---

### Post by mlind on 2006-06-05
[QUOTE=FireFusion]Thanks. I think I managed to install everything but being a newb to this sort of thing I don't know what to do next or how to access anything. Could you point me in the right direction of a full guide of something?

Thank you.[/QUOTE]

If it's not Ubuntu related, then Google is your best guide. Just by searching about
j2ee development using tomcat, mysql and jsp as search query, you should find
bunch of stuff. Try looking for "Hello world" JSP stuff, those usually include tomcat
or jetty setup too.

What I would do is to install development IDE next, preferably Eclipse with WTP
plugin and dependencies. WTP offers you easy way to handle servlet container,
and Eclipse a powerful development environment. WTP also offers features
for easier JSP development.

Mysql has numerous tools, graphical or command-line, to handle databases.

---

