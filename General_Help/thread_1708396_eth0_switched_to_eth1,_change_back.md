---
title: "eth0 switched to eth1, change back?"
date: 2011-03-16
forum: General Help
---

### Post by ondemanddesign on 2011-03-16
Alright, the situation is as follows: 

I am setting up my first Linux based crash plan. One of my goals was to corrupt a Ubuntu Server installation by removing directories (such as /var and /lib) along with messing up config files. 

After those files were tampered with I took an FSArchive image from a separate Ubuntu installation on a separate PC and transfered it onto a recovery CD via rsync over the network. I then restored the filesystem, everything was properly restored BUT I didn't have internet. I quickly did a

```
ifconfig -a
``` 

This showed eth0 did not exist, instead it was replaced with eth1. I then did:

```
sudo nano /etc/network/interfaces
```
and changed eth0 to eth1 followed by running ifup eth1.

This allows me to have internet, but I would like the interface to be eth0 for cross platform synchronization. Is there any way to easily change a network interface like this?

---

### Post by Mr_Bumpy on 2011-03-18
Find /etc/udev/rules.d/*-persistent-net.rules file (* is 70 on mine).  You can either delete the file or edit by deleting the eth0 line and edit the eth1 line to say eth0.

Hope this helps!

---

