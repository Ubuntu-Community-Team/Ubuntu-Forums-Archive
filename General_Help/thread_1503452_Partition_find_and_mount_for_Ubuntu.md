---
title: "Partition find and mount for Ubuntu?"
date: 2010-06-06
forum: General Help
---

### Post by searchfgold6789 on 2010-06-06
How do you get the famed Find and Mount software to work from within a Xubuntu machine? Will it work from Wine???


... and ...

:biggrin: does this site happen to be hosted by freeforums.org???
'night,
 - search

---

### Post by bodhi.zazen on 2010-06-06
What is the "famed find and mount software" you are wanting ?

Xubuntu will auto mount removable devices, CD, flash drives, etc.

It will also mount internal hard drives.

---

### Post by 4Orbs on 2010-06-06
```
sudo apt-get install pysdm
```
Copy and paste the above in a terminal and hit enter. After it finishes installing, look in the System menu for Storage Device Mgr.

---

### Post by bodhi.zazen on 2010-06-06
psydm is very nice, but FYI the OP is asking about Xubuntu and with Xubuntu Thunar will mount partitions and removable devices, so psydm is not needed.

---

### Post by searchfgold6789 on 2010-06-06
findandmount.com

---

### Post by 4Orbs on 2010-06-06
I agree with you 100% bodhi.zazen that pysdm is not necessary. I just happened to fall in love with it a long time ago and the romance is still hot. Old habits die hard.

---

### Post by bodhi.zazen on 2010-06-07
> **searchfgold6789 said:**
> findandmount.com

The closest thing I know of to findandmount in Linux is testdisk

testdisk should, IMO, be run from a live CD and it is in the Ubuntu repositories, so

```
sudo apt-get install testdisk
```

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by 4Orbs on 2010-06-07
There is also an applet for the xfce4 panel called Mount Devices. Right click on the panel and choose "Add Item" and the menu pops up with all the available launchers and applets, one of which is the Mount Devices applet. Looks convenient although I've never used it.

---

### Post by searchfgold6789 on 2010-06-07
I am looking for *data recovery *software!

---

### Post by bodhi.zazen on 2010-06-07
> **searchfgold6789 said:**
> I am looking for *data recovery *software!

did you look at testdisk ? testdisk does data recovery, as does photorec, which is included in testdisk.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

install testdisk on a live CD and let us know if you are having problems, we would need more information to provide more specific advice.

---

### Post by searchfgold6789 on 2010-06-07
kewl, I'll give testdisk a try :)
looks complicated :\
just my sort of thing :)

In the meantime I messed up my ubuntu install, good thing it was a fresh one!

---

### Post by bodhi.zazen on 2010-06-07
Again, you really should run testdisk from a live CD.

---

### Post by searchfgold6789 on 2010-06-07
Thaaaaaaannnnnnkkkk yooooooouuuuuuuuu!!!!!!!!!!!!!!!
One last thing. I copied the lost files to my linux disk. If i make a partition on one of my other hard disks, NTFS it, flag it as boot, and primary, copy the files to that, and plug it in to one of my desktops will it boot from the, uh, Windows I recovered? (scuse my french)

---

### Post by bodhi.zazen on 2010-06-07
> **searchfgold6789 said:**
> Thaaaaaaannnnnnkkkk yooooooouuuuuuuuu!!!!!!!!!!!!!!!
One last thing. I copied the lost files to my linux disk. If i make a partition on one of my other hard disks, NTFS it, flag it as boot, and primary, copy the files to that, and plug it in to one of my desktops will it boot from the, uh, Windows I recovered? (scuse my french)

You may or may not have problems with the recovery. 

Generally I just pull the data an reinstall the OS and honestly I am not very familiar with Windows, so I can not say for sure.

---

### Post by searchfgold6789 on 2010-06-07
I'll figure out a way. Thanks for the help.
:guitar:

---

