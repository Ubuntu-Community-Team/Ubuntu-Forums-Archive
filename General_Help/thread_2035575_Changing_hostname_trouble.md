---
title: "Changing hostname trouble"
date: 2012-07-30
forum: General Help
---

### Post by FerasMoalla on 2012-07-30
Hi

I have changed the hostname, by accessing the file /etc/hostname
It seems that there is something wrong going on as whenever I type sudo I get the error: 
 
sudo: unable to resolve host 

How is it possible to overcome this problem?

Thanks

---

### Post by efflandt on 2012-07-31
You also need to change your hostname in /etc/hosts which points to loopback IP 127.0.1.1 so Linux can find itself by your hostname.

If sudo is not actually working, you may need to boot live/install CD (or iso on bootable USB), mount the drive, and change it from there.

---

### Post by codemaniac on 2012-07-31
> **FerasMoalla said:**
> Hi

I have changed the hostname, by accessing the file /etc/hostname
It seems that there is something wrong going on as whenever I type sudo I get the error: 
 
sudo: unable to resolve host 

How is it possible to overcome this problem?

Thanks

Read the first link in the below thread .

[http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

### Post by BkkBonanza on 2012-07-31
Use the hostname command instead as it updates correctly.

sudo hostname mymachine

---

