---
title: "apt-get update question"
date: 2012-07-17
forum: General Help
---

### Post by mindlube on 2012-07-17
Hi all, my login banners says there are 6 security updates but I cannot seem to install them. What am I missing below?
> Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-generic x86_64)
...
6 packages can be updated.
6 updates are security updates.

Then I do this:
```
$ sudo apt-get update
...
Fetched 20.0 MB in 11s (1,715 kB/s)                                            
Reading package lists... Done

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

---

### Post by wojox on 2012-07-17
Dist upgrade:

```
sudo apt-get dist-upgrade
```

---

### Post by epikvision on 2012-07-17
Are you trying to upgrade your system to the development release or install new packages?

---

### Post by BBQdave on 2012-07-17
> **mindlube said:**
> Hi all, my login banners says there are 6 security updates but I cannot seem to install them. What am I missing below?


Then I do this:
[CODE]$ sudo apt-get update

$ sudo apt-get upgrade

If you are updating: sudo apt-get **update**

and I would suggest a reboot :)

---

### Post by QIII on 2012-07-17
```
sudo apt-get dist-upgrade
```

does not upgrade to the next version of Ubuntu.  It does what

```
sudo apt-get upgrade
```

does, with the addition of attempting to resolve dependency issues

---

### Post by Cheesemill on 2012-07-17
To be clearer,
```
sudo apt-get upgrade
```Will upgrade any packages that are **already** on your system to the newest versions.
Because installing a kernel update actually installs a **new** package on your system instead of upgrading the current kernel you need to use:
```
sudo apt-get dist-upgrade
```

---

### Post by QIII on 2012-07-17
> **BBQdave said:**
> If you are updating: sudo apt-get **update**

and I would suggest a reboot :)

That does not update any software.  It updates the sources list and what is available for upgrading.  In and of itself it does not update or upgrade apps or components.

It must be followed by

```
sudo apt-get upgrade
```or in this case

```
sudo apt-get dist-upgrade
```to actually get the latest apps and updates.

Please see [this](https://help.ubuntu.com/community/AptGet/Howto) wiki for details.

---

### Post by mindlube on 2012-07-21
Thanks for the replies all! I continued to do over a few days time:
sudo apt-get update
sudo apt-get upgrade
and eventually the warning on the banner went away. Maybe it was a temporary glitch, or the banner was outdated or something. 
I just did sudo apt-get dist-upgrade and it installed the latest kernel version too (still Ubuntu 12.04)
So I guess I'm all good :popcorn:

---

### Post by raja.genupula on 2012-07-21
mark the thread as solved from thread tools .

---

