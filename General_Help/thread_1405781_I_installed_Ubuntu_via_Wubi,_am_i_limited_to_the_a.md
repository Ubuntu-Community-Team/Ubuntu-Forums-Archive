---
title: "I installed Ubuntu via Wubi, am i limited to the amount of space?"
date: 2010-02-13
forum: General Help
---

### Post by Waveridr85 on 2010-02-13
I just tried adding my music from a portable hd and it says that there is not enough space in the destination.  What gives?  What can i do to fix this?

Thnx

---

### Post by Elfy on 2010-02-13
You will be limited to the amount of space you gave wubi when you installed it. Your windows should be availabel in /hosts.

You could expand the partition I think with lpvm - [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Waveridr85 on 2010-02-13
> **forestpiskie said:**
> You will be limited to the amount of space you gave wubi when you installed it. Your windows should be availabel in /hosts.

You could expand the partition I think with lpvm - [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Thanks for your help

---

### Post by Elfy on 2010-02-13
You might also be able to get yourself a small amount of roof by making sure all traash are empty and you can also clear the apt cache

```
sudo apt-get clean
```

---

### Post by Waveridr85 on 2010-02-13
> **forestpiskie said:**
> You might also be able to get yourself a small amount of roof by making sure all traash are empty and you can also clear the apt cache

```
sudo apt-get clean
```
I think I am just going to go with a full blown install.  I just bought the comp and it came with Vista.  Is there an easier way to go about this instead of completely formatting

---

### Post by Elfy on 2010-02-13
Use the vista disk management tool to shrink the existing partition (assuming you wish to keep it) then you can use the unallocated space to install ubuntu to.

Plenty of easy to read information here - [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by Waveridr85 on 2010-02-13
> **forestpiskie said:**
> Use the vista disk management tool to shrink the existing partition (assuming you wish to keep it) then you can use the unallocated space to install ubuntu to.

Plenty of easy to read information here - [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)


I dont think I will even need to dual boot to be honest

---

### Post by Elfy on 2010-02-13
Then boot the livecd and install - when you get to the partition part choose use whole disk and that is what it will do.

Make sure while you are using the livecd that your hardware all works - handy for that they are :)

Good luck

---

### Post by lenoirrichelieu on 2010-02-13
Before using entire disk take in consideration these:
-if you have a brand new laptop with Vista pre-installed then check if it has hidden recovery partition. Many of them come with a recovery partition for re-installing Vista. Maybe is a good idea to preserve that just in case.
 
-if is this the case then use only the partition where Vista is actually installed and not the entire disk

---

