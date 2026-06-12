---
title: "zend server problem"
date: 2009-12-08
forum: General Help
---

### Post by OmidPLUS on 2009-12-08
hi,
I recently installed zend-server, it removed the standard php5 package and installed its own packages, now I want to remove zend server from my ubuntu and install php5 package,
the problem is that I cannot do this, this is the result of following command:

```
sudo apt-get remove zend-server-php-5.2
```> (Reading database ... 263549 files and directories currently installed.)
Removing zend-server-php-5.2 ...
Stopping Zend Server 4.0.6 ..

E: Sub-process /usr/bin/dpkg exited unexpectedly
I guessed that the problem might be of stopping zend server, so I tried to do manually, but I received this error:

```
sudo /etc/init.d/zend-server stop
```> Stopping Zend Server 4.0.6 ..

Terminated
Please somebody helps me ...

---

### Post by OmidPLUS on 2009-12-08
Please someone helps me, I'm really stuck :-(

---

