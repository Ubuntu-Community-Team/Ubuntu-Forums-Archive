---
title: "Difficulty downloading splashy from synaptic"
date: 2009-10-18
forum: General Help
---

### Post by pgar23 on 2009-10-18
Hi,
  I am trying to download splashy because I found this awesome .jpg that I would like to make my own splash image out of it, but while I am trying to download splashy from the synaptic package manager, it throws me an error;
```

An ERROR occured:
the following details are provided:

E: /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_amd64.deb: trying to overwrite `/etc/lsb-base-logging.sh', which is also in package lsb-base

```

I manually searched the /etc/lsb-base folder and there are no files located in this folder.

Secondly, i tried running the package via /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_amd64.deb, the package installer says that there are broken dependencies. 

I already tried:
```
sudo apt-get update
```
and
```
sudo apt-get install -f
```
like it suggests...but still nothing fixed. 

I hope someone has advice or suggestion. Thanks in advance.

---

### Post by P4man on 2009-10-19
Its always a good idea to google on the exact error message. have a look here:
[https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/328089](https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/328089)

---

### Post by betlog on 2010-07-17
i am having a similar issue. Except I no longer want to install it (i am 10.04) i want it gone so it's not a spanner in the  cogs of kpackagekit/apt any more.
[http://ubuntuforums.org/showthread.php?t=1532808](http://ubuntuforums.org/showthread.php?t=1532808)

---

