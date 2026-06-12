---
title: "Apache-Tomcat binds only to IPv6"
date: 2010-05-21
forum: General Help
---

### Post by sickle on 2010-05-21
Hi,

We are trying to install Jasper Server 3.7 with Apache-Tomcat 5.5.20 bundle on Ubuntu 9.10. Usually, we only have to run the executable and reply to questions. For a reason that we ignore, for this server, tomcat is only listening on IPv6. We have other applications that listens to IPv4 without problem. Does somebody have an idea ?

---

### Post by dcstar on 2010-05-22
> **sickle said:**
> Hi,

We are trying to install Jasper Server 3.7 with Apache-Tomcat 5.5.20 bundle on Ubuntu 9.10. Usually, we only have to run the executable and reply to questions. For a reason that we ignore, for this server, tomcat is only listening on IPv6. We have other applications that listens to IPv4 without problem. Does somebody have an idea ?

Remove any other applications already using the port.

---

### Post by sickle on 2010-05-25
Thank you. Strangly, our problem is solved ! By magic, we are able to connect to jasperserver by IPv4 even if tomcat is listening with IPv6 ! It did not work at all friday, now it works.:confused:

---

