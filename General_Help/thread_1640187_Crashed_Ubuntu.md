---
title: "Crashed Ubuntu"
date: 2010-12-07
forum: General Help
---

### Post by k19_widowmaker on 2010-12-07
Hey guys, it's obvious that my ubuntu has crashed, all I need now is to recover my data, there are many important data that I need.... It would be better if there is a way to reinstall ubuntu without loosing my data.... But as I said, my priority is recover the data.....

---

### Post by Megaptera on 2010-12-07
Can you boot into a live CD (such as the one you installed Ubuntu from)? 
Don't install, use try Ubuntu, navigate to your docs etc on the hard drive & cut/paste to external media.

---

### Post by karthick87 on 2010-12-07
Have you tried photorec and test disc?

---

### Post by k19_widowmaker on 2010-12-07
> **Megaptera said:**
> Can you boot into a live CD (such as the one you installed Ubuntu from)? 
Don't install, use try Ubuntu, navigate to your docs etc on the hard drive & cut/paste to external media.


Yes I can, do u mean that I have to use the Ubuntu istallation cd and to use try Ubuntu? to be honest I can't remember if there was an option like this, buf if this what you mean I can give a try !!!

---

### Post by k19_widowmaker on 2010-12-07
> **karthick87 said:**
> Have you tried photorec and test disc?

I'm a beginner Ubuntu user, and  I don't know the program you are talking about ? can you tell me about it, and how to use it ?

thanks

---

### Post by karthick87 on 2010-12-07
Boot your system using a live cd and follow the steps in the following link.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by argedion on 2010-12-07
K-19 - You can boot the install cd this has a live version of ubuntu its the first option usually if you leave the keyboard alone it will boot automatically.

> Have you tried photorec and test disc?
The programs karthick talk about are here:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
WARNING!!! BACKUP YOUR DATA FIRST. Then use testdisk to see if there is a problem with the hard drive. testdisk is a poweful disk utility that can help recover from disk problems. If you are unsure of what your doing then do nothing these programs can do as much harm as they can good especially for the inexperienced user

---

### Post by msandoy on 2010-12-07
Boot from the live cd, and take a backup of your data. When reinstalling, choose manual partitioning, and make one swap partition, one root(/) partition about 10-15 GB, and the rest as one partition for /home. With a setup like that, you can reinstall the system on top of the old one, without loosing anything in /home. I always do it this way, since I have a habbit of fiddeling a bit too much with the system, and sometimes it dies on me. then it is faster to reinstall. :-)

---

