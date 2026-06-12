---
title: "What is /dev/mapper?"
date: 2011-01-02
forum: General Help
---

### Post by mblahay on 2011-01-02
A couple of months ago I was playing around with raid arrays and was able to create the raid devices in /dev.  Now mdadm forces me to create the devices in /dev/mapper. What is this directory?

---

### Post by ronparent on 2011-01-02
Welcome to the forum.

/dev/mapper is the directory that maps out the symbolic link for the so called fakeraid array(s) and its partitions. It is created by dmraid based on fakeraid meta data found on disks in your system which occurs when a MB raid chip is set active in bios. That is completely separate from linux software raid partitions created and maintained by mdadm. 

Dmraid is useful if you want to share raid partitions with windows. It is not normally compatible with md-x devices created for the linus software raid. Unless you are trying to operate side by side with windows installed to a raid the raid should be turned off in bios, raid meta data should be erased and dmraid uninstalled or the system booted with 'nodmraid'. Post if you have further question.

---

### Post by noah++ on 2011-01-02
Though I don't know how to account for it technically, I can say that hard links to LVM volumes on my encrypted disk live under **/dev/mapper** too.

---

### Post by Dave_L on 2011-01-02
ecryptfs also uses /dev/mapper.

---

### Post by ronparent on 2011-01-03
Great information - since my only prior knowledge was related to the sym links created by dmraid. 

As of 10.10 additional sym links have appeared in /dev labeled dm-x (0 to whatever) corresponding to each of the raid partitions. I have no insight yet if and how they will ultimately be used. Probing for these links during boot creates annoying script errors for the raid array(s) and any extended partition telling us that they do not contain valid file systems (no kidding)!

---

