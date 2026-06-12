---
title: "Heimdal KDC"
date: 2011-05-13
forum: General Help
---

### Post by vinnb on 2011-05-13
Hi,

I need instructions or pointers that tells me how to set up heimdal kdc on my ubuntu machine. 

Googled for answers but could not find any. Kindly help.

---

### Post by Lars Noodén on 2011-05-13
It's been a long time since I've done anything like that. IIRC, Heimdal is an implementation of Kerberos, so the instructions for MIT kerberos should also work fairly well.  Here's one for Heimdal:

[http://chschneider.eu/linux/server/heimdal.shtml](http://chschneider.eu/linux/server/heimdal.shtml)

---

### Post by vinnb on 2011-05-15
Thank you very much. I was able to set up KDC successfully. I have another query. Is heimdal limited only to ubuntu machines? Can i have a linux client make use of the Heimdal KDC that I have set up? If yes kindly let me know the procedure to configure a Linux machine as a Heimdal client.

Thanks in advance :)

---

### Post by Lars Noodén on 2011-05-16
> **vinnb said:**
> Thank you very much. I was able to set up KDC successfully. I have another query. Is heimdal limited only to ubuntu machines? 

Heimdal is available on many platforms. Further, it should interoperate with MIT Kerberos.  So that means that any client, if so configured, can user your servers.

> **vinnb said:**
> 
Can i have a linux client make use of the Heimdal KDC that I have set up? If yes kindly let me know the procedure to configure a Linux machine as a Heimdal client.
Thanks in advance :)

There's some [community documentation on kerberos](https://help.ubuntu.com/community/Kerberos#Client%20Configuration).  I'd start there.  Also look at the documentation for Pluggable Authentication Modules (PAM).

---

### Post by Asad Ali on 2012-04-14
Migration of Services from Ubuntu 8.04 toUbuntu 12.04.
We upgrade Ubuntu 8.04 toUbuntu 12.04.In our environment Ldap, Samba and Kerberos Heimdal are integrated with each other.(Single sign on authentication for Mail, OpenAFS and Domain login)
I restored Ldap through slapadd command.
Anyone can help me to migrate/restore kerberos heimdal database from Ubuntu 8.04 toUbuntu 12.04. 
I will be thankful.

---

