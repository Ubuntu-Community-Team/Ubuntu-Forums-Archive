---
title: "tomcat + mysql"
date: 2009-07-14
forum: General Help
---

### Post by luigifonti on 2009-07-14
In the past times I have set up and used the couple tomcat + mysql on different systems: Windows, Fedora... and they always worked together without problems, allowing my servlets to access mysql server on the same server.

Now I tried to use them under Ubuntu 9.04, using tomcat6 and mysql5.1,
but there is no way to let any servlet to access mysql.

I can access mysql using Java applications, but not with servlets.
What I always get is an access denied SqlException, even if in both cases I use the same mysql username and password.

Did somebody get them working ?
Luigi

---

### Post by SyL on 2009-07-15
> **luigifonti said:**
> In the past times I have set up and used the couple tomcat + mysql on different systems: Windows, Fedora... and they always worked together without problems, allowing my servlets to access mysql server on the same server.

Now I tried to use them under Ubuntu 9.04, using tomcat6 and mysql5.1,
but there is no way to let any servlet to access mysql.

I can access mysql using Java applications, but not with servlets.
What I always get is an access denied SqlException, even if in both cases I use the same mysql username and password.

Did somebody get them working ?
Luigi

First of all, a servlet should NOT directly connect to the database. This is a basic Java design best practice. 
So from you Servlet access an object which will do the job.

---

