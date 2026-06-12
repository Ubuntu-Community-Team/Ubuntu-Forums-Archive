---
title: "Deploying apps in Tomcat 6"
date: 2010-09-17
forum: General Help
---

### Post by Kinildson Persegueiro on 2010-09-17
Hi there!

     Tomcat 6 docs says that when you deploy an app, using tomcat web manager, the app goes to $CATALINA_HOME\webapps.

     Well, my app is not there, yet it works, it is accessible via browser...

     Where does Tomcat 6 put the app directory? 

Thanks!

PS. Programming forum was not accepting new threads...

---

### Post by Kinildson Persegueiro on 2010-09-17
up

---

### Post by calucifer on 2010-09-17
took me a while to figure out this one myself!

it puts them in /var/lib/tomcat6/webapps/ (which is CATLINA_BASE\webapps)

---

### Post by Kinildson Persegueiro on 2010-09-18
Thanks! :D

---

### Post by jdeal on 2010-12-26
Also thanks.  Took me all day off and on to get to this thread and discover the proper deployment directory.  Not obvious at all with the documentation (at least what I saw).

---

