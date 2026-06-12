---
title: "Add new role to Tomcat"
date: 2010-02-28
forum: General Help
---

### Post by kantu on 2010-02-28
I installed Tomcat6.0.24 on my system and i needed to add a manaager account , 
```
<role rolename="manager"/>
<user username="tomcat" password="s3cret" roles="manager"/>

```
This is the help given in Tomcat6 itself and though a user exists by this role i cannot login through that account , 
i Edited the file tomcat-users.xml in its conf DIR . Should i add user in any other file ? or what other modifications should be done ?

---

