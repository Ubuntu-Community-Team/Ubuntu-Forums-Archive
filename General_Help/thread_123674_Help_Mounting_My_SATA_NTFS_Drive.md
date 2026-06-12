---
title: "Help Mounting My SATA NTFS Drive"
date: 2006-01-30
forum: General Help
---

### Post by OrganicPanda on 2006-01-30
heya all, a classic case of moving from windows to linux and getting stuck on some trivial stuff.

anywho my problem is that kubuntu wont allow me to mount my sda because its allready mounted but only root can access it, whats the solution to this no doubt obvious dilema, do i use some command to change the access rights to the directory /dev/sda or do i remount somehow or is there something else todo

thanks in advance 

p.s i would kinda like sda to but mounted somewhere else, /dev/sda isnt a very nice place for it

---

### Post by Sutekh on 2006-01-30
You need to change the access to the folder where /dev/sda is mounted.

Best way is to create a folder to mount /dev/sda to.  You will have to add an entry to your /etc/fstab (mount information)

Have a read of this for all the steps you will need.
[Mounting Windows - ]("http://www.psychocats.net/linux/mountwindows.php")[by aysiu]("http://www.ubuntuforums.org/member.php?u=21941")

---

### Post by OrganicPanda on 2006-01-30
ahhh yes i see now, thank you kind sir/madam:cool:

---

