---
title: "Forward user to server based on URL"
date: 2011-03-18
forum: General Help
---

### Post by ondemanddesign on 2011-03-18
I need to know how to forward a user to a Microsoft IIS server under the SAME domain name (e.g. [www.MySite.com](www.MySite.com)) depending upon url parameter. My goal is to do this without using a subdomain (e.g. events.MySite.com). The diagram below depicts my goal. I want my linux server to decide whether to forward the user to an IIS server or serve them content from apache based on the url (e.g. [www.MySite.com/Events](www.MySite.com/Events)). Can this be done?

[IMG]http://farm6.static.flickr.com/5017/5537629925_3796c8ffe3.jpg[/IMG]

---

### Post by r-senior on 2011-03-18
I believe you can do it with AJP, the same as Tomcat. I've never done it with IIS, but I wrote a guide for Apache/Tomcat on Ubuntu here:

[http://explodingjava.blogspot.com/2010/03/configuring-apache-and-tomcat-on-ubuntu.html](http://explodingjava.blogspot.com/2010/03/configuring-apache-and-tomcat-on-ubuntu.html)

The Apache config would be the same, you'd just have to figure out how to enable an AJP connector in IIS.

---

### Post by ondemanddesign on 2011-03-18
> **r-senior said:**
> I believe you can do it with AJP, the same as Tomcat. I've never done it with IIS, but I wrote a guide for Apache/Tomcat on Ubuntu here:

[http://explodingjava.blogspot.com/2010/03/configuring-apache-and-tomcat-on-ubuntu.html](http://explodingjava.blogspot.com/2010/03/configuring-apache-and-tomcat-on-ubuntu.html)

The Apache config would be the same, you'd just have to figure out how to enable an AJP connector in IIS.

I need to hear from someone who has done this kind of thing specifically, this seems like a deep rabbit hole that will probably not work, there has to be something in place within Linux to do what I need right?

---

