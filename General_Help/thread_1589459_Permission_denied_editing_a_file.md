---
title: "Permission denied editing a file"
date: 2010-10-06
forum: General Help
---

### Post by DrReaper on 2010-10-06
I am setting up Postfix email server and I am supposed to edit a file smtpd.conf
I edit the file in /etc/postfix/sasl/ and I try to save it. I get an error permission denied. 

I expect this is a folder permission error. What should I do? Is there a way to open terminal with more rights or should I change the permissions on the folder?

More information: I browsed to the folder and it says I am not the root so I cannot change the permissions. 

I am running 10.04 32 bit. Not the server version.

---

### Post by whiskeylover on 2010-10-06
try 

```
sudo vim smtpd.conf
```

---

### Post by lisati on 2010-10-06
When editing configuration files, it's a common safety requirement that you need "super user" privileges (a.k.a. "root" privileges) to be able to save your changes. One way to temporarily acquire the needed privileges is to prefix the command you use with "sudo". For example: ```
sudo nano /etc/postfix/sasl/smtpd.conf
``` or ```
gksudo gedit /etc/postfix/sasl/smtpd.conf
```

---

### Post by DrReaper on 2010-10-06
Thanks a lot I was missing the sudo command and the explanation as it helps with my overall understanding.

---

