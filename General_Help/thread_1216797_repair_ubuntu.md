---
title: "repair ubuntu"
date: 2009-07-18
forum: General Help
---

### Post by applehead on 2009-07-18
Hi all.

I kicked my keyboard lead, machine shut down, now I can't bot from my HD.

I can access it by using a live CD but can't copy files from the drive to a memory card.

Is there some way I can repair the install and keep the files?

---

### Post by roquin on 2009-07-18
upload them to you mail on line then fix you operating system and download them back

---

### Post by Herman on 2009-07-18
I don't know why you wouldn't be able to copy your files to some kind of backup media if you can access them, unless you have file permissions problems stopping you from writing to your backup media.
What's a 'chip'?
You might need to chmod the mount point or use a sudo command. Something like this might work,
```
sudo cp -Rav /media/home/* /media/disk/
```Where: '/media/disk/' is your mount point.
That should make a backup of your user files. Check to make sure the hidden files were included, if you want any of those.

Most times, if your operating system has been shut down improperly, it's simple for anyone to fix the file system. We used to need to know some file system commands, but now almost anyone can do it with GParted in the Ubuntu Live CD.
Always leave your file systems unmounted until after the file system check, never try to run a file system check in a file system while it's mounted.

[LIST=1]
[*]Boot your Live CD, open Gnome Partition Editor and right-click on the partition you want checked. In Hardy Heron it is 'System-->'Administration'-->'Partition Editor'.
[*]Select 'check' from the right-click menu. If 'check' is greyed out you might need to select 'unmount first, then click 'check'.
[*]Click the 'Apply'  check mark button up on the toolbar.
[*]Click the 'Apply' button in the confirmation pop-up window
[*]Watch the reciprocating bar for a few minutes, a very large file system may take a while
[*]Click on the 'Details' triangle to expand the window
[*]Click on the triangle in front of 'Check and repair file system (ext3_ on ....)' for details
[*]Be sure to fully expand all details and read what has been done. If it's the Ext3 file system, GParted will have calibrated your file system and run e2fsck -f -y -v on it for you, and has run resize2fs for you to make sure your file system is the right size to fill your partition.
[/LIST]
That will probably fix it and make your operating system bootable again if it was a file system problem.

---

### Post by applehead on 2009-07-19
Thanks for your reply Herman.

It seems that it's only password protected docs that I can't copy.  Even though I know the passwords, it wont let me do anything with them!  I tried sudo cp -Rav /media/home/* /media/disk/  although I'm almost useless with the command line. It seems to have copied a very old version of a document that I need. so it's copied the document but when I open it, it's in the same state as it was in March.
 When I use sudo, shouldn't it ask me for a password?  
 Any ideas how I can access that document?

---

### Post by applehead on 2009-07-19
just tried G parted, no joy, still wont boot.

Is there any way to re install without loosing your files?

---

### Post by philcamlin on 2009-07-19
boot into live cd backup 
to thumb drive 

reinstall :(

---

### Post by applehead on 2009-07-19
this is what I get when I try sudo cp -Rav   

 cp: failed to preserve ownership for `/media/disk/money.ods': Operation not permitted

---

### Post by applehead on 2009-07-19
> **philcamlin said:**
> boot into live cd backup 
to thumb drive 

reinstall :(

trying to... can't access one of my documents that I need. it's password protected.

---

### Post by applehead on 2009-07-20
I've salvaged what I could and re installed.

---

### Post by elliotn on 2009-07-20
Strange but for me I always copy an backup usin live cd

---

### Post by elliotn on 2009-07-20
> **applehead said:**
> just tried G parted, no joy, still wont boot.

Is there any way to re install without loosing your files?

Use gparted to partition your drive, making sure that u leave enough space to install ubuntu. Then install ubuntu on the new partition. Wala u have your files in a separate partition.

---

