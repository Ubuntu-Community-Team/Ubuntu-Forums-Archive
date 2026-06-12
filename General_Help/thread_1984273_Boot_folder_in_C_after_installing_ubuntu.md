---
title: "Boot folder in C: after installing ubuntu"
date: 2012-05-21
forum: General Help
---

### Post by neophyte02 on 2012-05-21
I just installed ubuntu but after doing that I got folders like boot, boot-sav and files like bootmgr, grldr e.t.c in my c:
 
When I checked disk management it is showing ubuntu drives also. As far  as i know ubuntu drives(ext4) doesn't get recognized by windows. What's  wrong with it?
 
And my system reserved drive is also being displayed in windows explorer.
 
What happened to my windows? Please help

---

### Post by kanikilu on 2012-05-21
How did you install Ubuntu? It sounds like you used Wubi (Windows Ubuntu Installer). Is that right? If so, Wubi does not create a separate ext4 partition, and Ubuntu effectively lives in the Windows partition. I've never used it, but I'd imagine this would explain the "mysterious" files showing up in Windows Explorer...

---

### Post by bcbc on 2012-05-21
> **kanikilu said:**
> How did you install Ubuntu? It sounds like you used Wubi (Windows Ubuntu Installer). Is that right? If so, Wubi does not create a separate ext4 partition, and Ubuntu effectively lives in the Windows partition. I've never used it, but I'd imagine this would explain the "mysterious" files showing up in Windows Explorer...

No, Wubi doesn't create boot or boot-sav folders. And it doesn't add the grldr (grub4dos). The only 'mysterious' files created by Wubi (not really mysterious) are: wubildr.mbr, wubildr, and the folder \ubuntu

This is not related to installing ubuntu either in a dual boot. Maybe there was some other software used?

PS you will see the Ubuntu partitions in Disk management but they will show as "Healthy" but no other info such as the file system.

---

### Post by kanikilu on 2012-05-21
Well, there you go - never used Wubi. Anyways, I was just guessing on the Wubi thing. The OP didn't specify the method of installation or really give much detail...

In fact, a search came up with a post from the OP on a Windows forum a couple weeks ago, and someone there had an interesting theory:

[http://www.sevenforums.com/general-discussion/228164-boot-folder-c-after-installing-ubuntu.html#post1910221](http://www.sevenforums.com/general-discussion/228164-boot-folder-c-after-installing-ubuntu.html#post1910221)

---

### Post by bcbc on 2012-05-21
Ubuntu isn't supposed to install grub in the windows boot partition anymore (grub had some checks put in to prevent this, but maybe it's broken again). If that does happen it would create the extra \boot folder but definitely wouldn't add grldr so I suspect it's probably something else.

---

### Post by oldfred on 2012-05-21
I think boot-sav is from Boot-repair, if you ask it to back things up.

Someone said the grub4dos install is from illegal installs of Windows. We always suggest to remove it.

But grub still can be installed to all partitions. I still use grub to boot a Windows repairUSB formated NTFS. Grub is in same folder as /Boot/BCD. But in most Windows installs it creates major problems if duplicate /boot folders are created.

---

### Post by neophyte02 on 2012-05-22
I didn't used wubi to install ubuntu. And I used boot-repair to repair grub

---

### Post by bcbc on 2012-05-22
> **neophyte02 said:**
> I didn't used wubi to install ubuntu. And I used boot-repair to repair grub

In that case I suggest you file a bug on boot repair: [https://bugs.launchpad.net/boot-repair/+filebug](https://bugs.launchpad.net/boot-repair/+filebug)

Installing grub to a Windows partition is not a great idea. It can overwrite the Windows bootsector and prevent Windows booting. Even if it doesn't overwrite the bootsector, if can cause issues if it creates a duplicate \boot folder (different case but Windows is case-insensitive). You were probably lucky that you had a separate boot partition but this isn't always the case.

---

### Post by YannBuntu on 2012-05-22
Hello
Boot-Repair automatically creates a "/boot-sav" folder in all system partitions. This folder contains a backup of your MBRs, partition tables, and logs.
Why not only inside Linux partitions? because this app is aimed at repairing access to all systems, whatever the config (even Windows monoboot).
Can I delete this folder safely? Yes, but you may want to create a backup before.

Concerning the other folders/files, please create a bug report as suggested by bcbc, and attach to it the ZIP file that you obtain by running Boot-Repair -> Advanced options -> Backup the partition tables(..).

---

