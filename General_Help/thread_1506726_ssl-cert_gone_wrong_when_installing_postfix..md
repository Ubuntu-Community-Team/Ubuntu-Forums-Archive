---
title: "ssl-cert gone wrong when installing postfix."
date: 2010-06-10
forum: General Help
---

### Post by ppp0 on 2010-06-10
Hello evereybody!
So here is my situation:
i cant install postfix on debian because of dependency or ssl-cert cant be configured:

```

Preconfiguring packages ...
Selecting previously deselected package postfix.
(Reading database ... 63444 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.5.5-1.1_i386.deb) ...
Processing triggers for man-db ...
Setting up ssl-cert (1.0.23) ...
dpkg: error processing ssl-cert (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postfix:
 postfix depends on ssl-cert; however:
  Package ssl-cert is not configured yet.
dpkg: error processing postfix (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ssl-cert
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Sooo... Postfix cant be installed because of ssl-cert cant be configured. But why? And even when installing ssl-cert manually - goes error...

How could i just correct this mistake ?
:confused:

PS: This is new server and i'm setuping it. All dependencies for ssl-cert are in place and packages installed...

---

### Post by ppp0 on 2010-06-11
isn't there's really no solution ?

---

### Post by dcstar on 2010-06-11
> **ppp0 said:**
> Hello evereybody!
So here is my situation:
i cant install postfix on debian because of dependency or ssl-cert cant be configured:

```

Preconfiguring packages ...
Selecting previously deselected package postfix.
(Reading database ... 63444 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.5.5-1.1_i386.deb) ...
Processing triggers for man-db ...
Setting up ssl-cert (1.0.23) ...
dpkg: error processing ssl-cert (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postfix:
 postfix depends on ssl-cert; however:
**  Package ssl-cert is not configured yet**.
dpkg: error processing postfix (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ssl-cert
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

sudo dkpg-reconfigure ssl-cert
```

---

### Post by ppp0 on 2010-06-12
Ups 

```

# dpkg-reconfigure ssl-cert
/usr/sbin/dpkg-reconfigure: ssl-cert is broken or not fully installed

```

---

### Post by dcstar on 2010-06-12
> **ppp0 said:**
> Ups 

```

# dpkg-reconfigure ssl-cert
/usr/sbin/dpkg-reconfigure: ssl-cert is broken or not fully installed

```

Then totally remove it, delete the package out of the apt cache and reinstall it.

---

### Post by ppp0 on 2010-06-13
> **dcstar said:**
> Then totally remove it, delete the package out of the apt cache and reinstall it.

same error:

```
apt-get install ssl-cert       
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ssl-cert
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.1kB of archives.
After this operation, 98.3kB of additional disk space will be used.
Get:1 http://ftp.mgts.by lenny/main ssl-cert 1.0.23 [13.1kB]
Fetched 13.1kB in 0s (139kB/s)
Preconfiguring packages ...
Selecting previously deselected package ssl-cert.
(Reading database ... 63435 files and directories currently installed.)
Unpacking ssl-cert (from .../ssl-cert_1.0.23_all.deb) ...
Processing triggers for man-db ...
Setting up ssl-cert (1.0.23) ...
dpkg: error processing ssl-cert (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ssl-cert
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

