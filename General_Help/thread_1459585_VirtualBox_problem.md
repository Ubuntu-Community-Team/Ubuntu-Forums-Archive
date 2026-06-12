---
title: "VirtualBox problem?"
date: 2010-04-21
forum: General Help
---

### Post by HHx66 on 2010-04-21
I had virtual box installed and running fine, I restarted my machine, and now when I try to run anything I get this error:

```
Kerner driver not installed (rc=.1908) Please install the virtualbox-ose-source package
```

However, that package IS installed, atleast according to dpkg and Synaptic, so what do I do to fix this?

---

### Post by carl4926 on 2010-04-21
sudo /etc/init.d/vboxdrv setup

---

### Post by HHx66 on 2010-04-21
Says it can't be found.

---

### Post by carl4926 on 2010-04-21
You should follow this
[http://ubuntuforums.org/showthread.php?t=1074160](http://ubuntuforums.org/showthread.php?t=1074160)

---

### Post by linden940 on 2010-04-21
DONT INSTALL THE ONE FROM THE UBUNTU SOFTWARE CENTER!!!!!!!!!!!!!!!!!!! YOU WILL BE VERY SORRY

just a simple warring....the one from the software center dos not have USB able on it....you HAVE to go to sun website and download it

---

### Post by HHx66 on 2010-04-21
Okay, thanks for the information. That worked. (I downloaded and installed the PUEL edition)

---

