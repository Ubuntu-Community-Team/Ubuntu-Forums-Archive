---
title: "How to install several Tomcat instances?"
date: 2010-05-19
forum: General Help
---

### Post by putkis on 2010-05-19
I need to have two instances of Tomcat 6 running on Ubuntu 10.04. I know it should be doable pretty simply by something like:

[LIST]
[*]copy /var/lib/tomcat6 to /var/lib/tomcat6-2
[*]modify ports in /var/lib/tomcat6-2/conf/server.xml
[*]copy /etc/init.d/tomcat6 to /etc/init.d/tomcat6-2
[*]modify /etc/init.d/tomcat6-2...
[/LIST]

...but my problem is that I'm unsure what I should modify in /etc/init.d/tomcat6-2. Changing the NAME in the beginning of the file clearly is not enough.

(I'm aware that there is tomcat6-new-instance but I don't want to create instances for users.)

I'm using Ubuntu 10.04 and installed 6.0.24 using apt-get.

---

