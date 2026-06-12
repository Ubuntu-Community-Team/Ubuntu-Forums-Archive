---
title: "Can't enter manager page in Tomcat"
date: 2010-06-19
forum: General Help
---

### Post by guyafe on 2010-06-19
Hi All
I tried to enter the manager page in tomcat 6, and although I entered the correct user-name and password, I still get a message that it is incorrect.
Here is my tomcat-users file which is basically copy-pased from another place in this forum. 
```

<?xml version='1.0' encoding='utf-8'?>
<tomcat-users>
  <role rolename="manager"/>
  <role rolename="tomcat"/>
  <role rolename="role1"/>
  <user username="both" password="tomcat" roles="tomcat,role1"/>
  <user username="tomcat" password="tomcat" roles="tomcat"/>
  <user username="test" password="test" roles="manager"/>
  <user username="role1" password="tomcat" roles="role1"/>
</tomcat-users>
```I tried all the advises in this forum but nothing helped.
Is it possible that from some reason Tomcat doesn't read the correct file?

Thanks
Guy

---

