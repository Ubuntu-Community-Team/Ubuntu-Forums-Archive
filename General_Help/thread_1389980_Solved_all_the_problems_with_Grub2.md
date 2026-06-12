---
title: "Solved all the problems with Grub2"
date: 2010-01-25
forum: General Help
---

### Post by Quarkrad on 2010-01-25
Whether it is reinstalling an image (either Ubuntu or windows) or reinstalling from scratch out of frustration I have never ending problems reinstalling grub2 to get access to my system(s).  Sometimes one method works sometimes not (why? It is frustrating when one time a set of commands work but sometimes not).  I have gone round and round in circles using about three or four very very similar methodologies sometimes it works sometimes not!!!!!!!!  So, my solution to sort all this out is to put grub2 in its own partition (one site suggested this).  It seems logical to me, if grub2 is in sda1 then surely I can reinstall backup images for sda2 or sda3 at will and the grub2 boot loader will be unaffected.   I'm not sure what will happen when there is a grub update from the Update Manager though. Do you think putting grub2 in its own partition will solve the problem?  (Please don't tell me to reinstall grub2 properly because there are many places - including Ubuntu Wiki type pages - that just do not work consistently.  It is all very well saying this page works - yes it does - but not always the 2nd or 3rd time you use it!!).  At the end of the day, reinstalling Linux Grub2 boot loader is not a simple exercise because it does not consistently work.  Normally I land up reinstalling the OS from Scratch.

---

### Post by rnerwein on 2010-01-25
hi
that's what i did. i have vista, suse, ubuntu and solaris running on my box. got all the bootloader installed in their own partition. using the suse bootloader to call the other bootloader (it's still the good old menu.lst)
title Ubutu
    root=(hd0,7)
    chainloader +1

title solaris 10
    rootnoverify (hd1,0)
    chainloader +1

title windows vista
    rootnoverify (hd0,5)
    chainloader (hd0,1)+1

ok i have to hit return twice but never get trouble with updates (suse i don't touch) if something goes wrong i just mount the other partitions and can confortable make changes.
ciao

---

### Post by blegs38552 on 2010-01-25
Unfortunately, I have found that there are times that the only way to solve Ubuntu problems is to reinstall the entire O/S. Since I run Ubuntu out of Windows 7 (WUBI install), this is a relatively painless, albeit time consuming procedure. When I had 9.04 (and 8.04) running on a separate partition, I had to erase the partition, and repair the Windows MBR using bootrec.exe on the recovery console. 

I guess that it is experiences like this that tell me that Linux is not ready for prime time, at least as a sole operating system. I still use Win 7 primarily, since it is much better for financial record keeping (Quicken) and tax preparation (TurboTax). I know that I could try running these out of WINE, but sorry, I just don't trust Linux that much, plus running backups to a networked drive would be a major problem.

---

### Post by Quarkrad on 2010-01-25
Pity - I love Ubuntu and use it 99% of the time but after 12 months use I must confess failure re Grub2.  Perhaps I mess around too much but I need something where after reinstalling an image (Clonezilla) I can easily re use the system.  In theory re-installing Grub2 looks (and is???) simple, only a few commands, but it does not work every time and like now - I'm stuck again.  Oh no - not another Ubuntu reinstall!  Can we not step backwards and have Grub1?

---

### Post by amgalitz on 2010-01-25
so far what seems working for me is to have several installations of Ubuntu, each with their own grub2. One is mainly to control the grub menu with the standard grub command. This can be 6GB (I allocate 9-10) if you keep it clean just with updates. This way you can mount your other installations to work on their configuration files or even **chroot** into them. 

The others partitions/installation are for production/testing. The most recent ubuntu installation in which you used the advanced option to set which drive gets grub2 installed done ends up controlling how grub works. After re-imaging an Ubuntu installation partition or changing a hard drive I do several steps:

[LIST]
[*]Make sure each partiton has a uniques label and use LABEL=...  in /etc/fstab rather than UUID (or sdx)
[*]Check that /etc/default/grub looks good
[*][Boot into each installation and run
[*]```
sudo install-grub
```
[*]If you have added/removed drives to your system and install-grub throws errors about drives, you may need to correct /boot/grub/device.map (see comment below)
[*]If you have added or moved drives around, check their boot order in you motherboard bios on your first reboot.
[/LIST]

Also you can use the line in /etc/default/grub:
```
GRUB_DEFAULT=  
``` through remote terminal or remote desktop with **startupmanager** to control which menu item is defaulted to. Grub counts the first menu item as 0 or you can enter the exact menu title. I find startupmanager easier. You need install startupmanager but once in System | administration, it gives you what your initial grub menu will look like and you can pick the default entry. (I use **freenx** and **nxclient**). 

Other options are here: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

COMMENT: If /boot/grub/device.map has more drives than are present, grub has failed to boot giving an error about the mising drive having incorrent size (or something like that). I had taken a few drives out for testing and only needed to change from:

/boot/grub/device.map```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde
```to:

/boot/grub/device.map```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```

Seems grub really did not like having more drives in the map then were physically present. I've moved drives around and changed their order in the motherboard BIOS but the device.map relationships haven't changed. I just now make sure that only the OS containing drives are listed in the device map and keep the data only drives on higher sata ports. Perhaps someone who truly understands how device.map fits in can point to a good tutorial, but this worked after copying an image from a system configuration with more drives to a system with fewer drives.

Hope this helps.

---

