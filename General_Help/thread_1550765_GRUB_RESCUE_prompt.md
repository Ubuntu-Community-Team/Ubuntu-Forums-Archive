---
title: "GRUB RESCUE prompt"
date: 2010-08-11
forum: General Help
---

### Post by anand1298 on 2010-08-11
Hi,

I recently installed 'ubuntu inside windows'...
It installed successfully...
Then i booted into ubuntu and updated the same using 'update manager'...
During the 'installation' stage, it asked me whether i want to 'update my grub' for which i selected 'yes'...
After installation, my computer got restarted and after restarting, instead of showing the boot menu(the menu which allows me to select whether i want to boot into windows or ubuntu), there was a prompt like, 'grub rescue>'...
I am stuck here...
I try all commands and only 'ls' seems to work(after typing 'ls' it shows my bootable partitions like 'fd0', 'hd0')...

Please help to fix this problem... I don't know how else to proceed after this prompt...

---

### Post by DFlame on 2010-08-11
Just to clarify, were you running Ubuntu as an app inside Windows (like [this)](http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows) or did you use something called [Wubi](http://wubi-installer.org/)?

Also, what version of Windows were you running?

---

### Post by Thomas Garman on 2010-08-11
Just reinstall Grub following these instructions.  It is actually VERY simple once you see what they are telling you to do...
 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by de Bacon on 2010-08-11
I have had similar issues.  Though I don't do duel boot with windows.  Though I have several HDDs and one has the older ubuntu 8.04 while I prefer using 10.04 (on a different HDD).  At first mine worked fine, then after some update it didn't any more.  

What I had to do was at initiation of start up (immediately after the beep) press the escape key, it took me to a post screen that allowed me to choose which drive (at partition mount point) to start.  Then it would start.  

Eventually I had to disconnect all but the HDD with 10.04, start (no problem at all) then shut down, at that time I reconnected one HDD, started again... until all 4 of my HDDs were finally connected again.  That resolved my problem, though I don't know if it would help you.

I too don't know what you mean about loading ubuntu "within windows."  But then I don't use windows any more :)

Best of luck

---

### Post by bcbc on 2010-08-11
> **anand1298 said:**
> Hi,

I recently installed 'ubuntu inside windows'...
It installed successfully...
Then i booted into ubuntu and updated the same using 'update manager'...
During the 'installation' stage, it asked me whether i want to 'update my grub' for which i selected 'yes'...
After installation, my computer got restarted and after restarting, instead of showing the boot menu(the menu which allows me to select whether i want to boot into windows or ubuntu), there was a prompt like, 'grub rescue>'...
I am stuck here...
I try all commands and only 'ls' seems to work(after typing 'ls' it shows my bootable partitions like 'fd0', 'hd0')...

Please help to fix this problem... I don't know how else to proceed after this prompt...

You 'installed within windows' i.e. used wubi. The first boot menu you normally see when you boot contained "Windows and Ubuntu". The second menu you saw after selecting Ubuntu was the Grub menu.

If all the above is true, then you have installed grub2 to your drive Master boot record (MBR) and have overwritten the windows bootloader, which is what you need with wubi installs.

So replace the windows bootloader using [this guide]("http://ubuntuforums.org/showthread.php?t=1014708") (scroll down to "How to restore the Windows XP Bootloader" or Vista/7 depending on the version of windows you have).

If you don't have windows disks, you can fix it from an ubuntu live CD as well. Let me know if you need this.

Edit: here's the bug report [https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

---

### Post by anand1298 on 2010-08-12
> **bcbc said:**
> You 'installed within windows' i.e. used wubi. The first boot menu you normally see when you boot contained "Windows and Ubuntu". The second menu you saw after selecting Ubuntu was the Grub menu.

If all the above is true, then you have installed grub2 to your drive Master boot record (MBR) and have overwritten the windows bootloader, which is what you need with wubi installs.

So replace the windows bootloader using [this guide]("http://ubuntuforums.org/showthread.php?t=1014708") (scroll down to "How to restore the Windows XP Bootloader" or Vista/7 depending on the version of windows you have).

If you don't have windows disks, you can fix it from an ubuntu live CD as well. Let me know if you need this.

Edit: here's the bug report [https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

OMG, thanks dude... I think yours will work... Definitely my windows bootloader must have been the problem... Thank you so much dude... I wish i can try it out... But i reinstalled my XP SP3 again and ubuntu again(did not update my grub this time)... Its working... Thanks 'bcbc'...

---

### Post by pikipadfoot on 2010-08-14
*If you don't have windows disks, you can fix it from an ubuntu live CD as well. Let me know if you need this.*



can you help me with this pls?

---

