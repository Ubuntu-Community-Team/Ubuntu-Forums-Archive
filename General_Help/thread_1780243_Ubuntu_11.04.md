---
title: "Ubuntu 11.04"
date: 2011-06-11
forum: General Help
---

### Post by Caali on 2011-06-11
Hey guys, when my computer was upgrading the packages it crashed with like 30 seconds left. On the reboot, the login screen was blue and it didn't have any accounts listed, I had to click other and sign in. when I hit log in, it freezes at that screen, the desktop environment doesnt launch. I have to click alt + ctrl + del in order to log out. I've tried going into system recovery, cleaning, repairing packages, and changing graphics dosnt work. Any ideas what I can do, I've tried all kinds of apt-get commands from the root terminal in recovery and dkpg commands too. Any ideas? Anyone else have this problem.

Additional info:
My computer has been freezing recently and I don't know what was causing it.

Posted from my iPod.

---

### Post by Caali on 2011-06-11
+ Bump + 

Help Please

---

### Post by Caali on 2011-06-11
Now it can't get to the login screen unless via failsafeX in recovery

Help ~

---

### Post by Caali on 2011-06-11
Is there any way I can reinstall Linux, someone please reply.

---

### Post by Caali on 2011-06-11
Bump

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **Caali said:**
> Hey guys, when my computer was upgrading the packages it crashed with like 30 seconds left. On the reboot, the login screen was blue and it didn't have any accounts listed, I had to click other and sign in. when I hit log in, it freezes at that screen, the desktop environment doesnt launch. I have to click alt + ctrl + del in order to log out. I've tried going into system recovery, cleaning, repairing packages, and changing graphics dosnt work. Any ideas what I can do, I've tried all kinds of apt-get commands from the root terminal in recovery and dkpg commands too. Any ideas? Anyone else have this problem.

Additional info:
My computer has been freezing recently and I don't know what was causing it.

Posted from my iPod.

I hope you did regular backups like every user knows they need to do, regardless of whatever OS they use??? 

Try a reinstall. This time try 10.10 on your particular system:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

I've had much better success rates with it.

And please please stick with a hardwired connection if your WIFI connection is flakey.  You can corrupt your entire system by having a bad signal during an important update or major upgrade.  Keep that in mind. :)

I always use a hardwired ethernet to do my upgrades and major updates..  If your system is important to you, then use one.  You won't have to worry about them as much with the older releases of Ubuntu once you have them done initially at the beginning.  Just my two cents and advice for you.

---

### Post by Caali on 2011-06-11
> **linuxinstalledfromhdd said:**
> I hope you did regular backups like every user knows they need to do, regardless of whatever OS they use??? 

Try a reinstall. This time try 10.10 on your particular system:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

I've had much better success rates with it.

And please please stick with a hardwired connection if your WIFI connection is flakey.  You can corrupt your entire system by having a bad signal during an important update or major upgrade.  Keep that in mind. :)

I always use a hardwired ethernet to do my upgrades and major updates..  If your system is important to you, then use one.  You won't have to worry about them as much with the older releases of Ubuntu once you have them done initially at the beginning.  Just my two cents and advice for you.

How do you re install? I have the disk but do I install over the current OS or do I make a new install and copy over my files?

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **Caali said:**
> How do you re install? I have the disk but do I install over the current OS or do I make a new install and copy over my files?

You don't have to install over it. It will resize your existing partition and make the space needed to do a "side-by-side" installation with 10.10 installation disc or live bootable USB Flash Drive of Ubuntu 10.10.. That way you can do a data migration of your data from your previous installation in case you didn't do a backup of your work.

---

### Post by wildmanne39 on 2011-06-11
> **Caali said:**
> How do you re install? I have the disk but do I install over the current OS or do I make a new install and copy over my files?
Hi, you can do as the other post suggested and do a side by side then you will have to change partitions to reclaim that space from the previous install, when you do that if the partitions are in the wrong place you will have to reinstall grub. I recommend reformatting and getting rid of the old install, unless you have files on it you can not live without,if so you can probably recover them using the livecd before you reinstall.

---

### Post by Caali on 2011-06-11
> **wildmanne39 said:**
> Hi, you can do as the other post suggested and do a side by side then you will have to change partitions to reclaim that space from the previous install, when you do that if the partitions are in the wrong place you will have to reinstall grub. I recommend reformatting and getting rid of the old install, unless you have files on it you can not live without,if so you can probably recover them using the livecd before you reinstall.

How would you go about making a Live CD? I have an installation disk. Are you talking about the "Try Ubuntu" button?

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **Caali said:**
> How would you go about making a Live CD? I have an installation disk. Are you talking about the "Try Ubuntu" button?

Yes, and I would try using 10.10, but not 11.04.

---

### Post by wildmanne39 on 2011-06-11
> **Caali said:**
> How would you go about making a Live CD? I have an installation disk. Are you talking about the "Try Ubuntu" button?Hi, yes and you can use the try mode to check it everything out before you decide to reinstall.

---

