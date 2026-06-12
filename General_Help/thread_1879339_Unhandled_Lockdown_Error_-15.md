---
title: "Unhandled Lockdown Error -15"
date: 2011-11-11
forum: General Help
---

### Post by Umunthu on 2011-11-11
Hello all.

I installed iOS 5 onto my iPod when it came out, and ever since I have been unable to mount it on Ubuntu 11.10. Instead, I always get the Unhandled Lockdown Error -15. I have searched for discussions by users with the same problem, but haven't found anything yet. I've tried the usual solutions for other lockdown errors, but nothing has worked so far. Any help would be appreciated.

---

### Post by dino99 on 2011-11-11
some solutions there:

[https://bugs.launchpad.net/ubuntu/+source/libplist/+bug/877440](https://bugs.launchpad.net/ubuntu/+source/libplist/+bug/877440)

---

### Post by jdamianb on 2013-02-13
This works for me:

iPod Touch (3th generation) w/ iOS 5.1.1 on Ubuntu 11.10

1. $ sudo apt-get install libimobiledevice-utils
2. $ rm ~/.config/libimobiledevice/*
3. $ idevicepair unpair && idevicepair pair
4. unplug and plug in

JCrx,

---

### Post by oldos2er on 2013-02-13
Old thread closed.

---

