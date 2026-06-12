---
title: "Copying Home directory to USB drive---Error"
date: 2010-04-15
forum: General Help
---

### Post by tperwez on 2010-04-15
Hi,

I am getting ready to upgrade from Ubuntu 8.10 to 9,04 (I am a bit behind, I know). I was advised on this forum to just drag my home folder to a USB drive to back up and it should copy all the files (including hidden ones).

When I tried this, I get the error that Symbolic links cannot be created. Should I worry about this? Would this effect my backup in some fashion?

I would appreciate any advice. Regards,

Tariq

---

### Post by ajgreeny on 2010-04-15
It will really depend on what those symbolic links are.

Just out of interest, I used to get several errors when I used rsync to backup home to a fat32 USB disk, and while it did work without any major difficulties, as far as the backup was concerned, I decided to format the USB disk to ext3, since when I have not seen any errors at all.  I do not know if your problem is related to that, but thought it worth the comment.

I do not have windows, only linux OSs, so there is no real need for me to have a fat32 disk, but if you dual boot, you may need to either keep fat32, or if the USB disk is big enough, divide it into two partitions, one of each file system.

---

### Post by WinterRain on 2010-04-15
Check the backup and compare it to the original. If the hiiden folders and regular folders are intact, I wouldn't worry about it.

---

### Post by egalvan on 2010-04-15
> **tperwez said:**
> Hi,

I am getting ready to upgrade from Ubuntu 8.10 to 9,04 (I am a bit behind, I know). I was advised on this forum to just drag my home folder to a USB drive to back up and it should copy all the files (including hidden ones).

Be aware that Microsoft file systems (vFAT, NFS) DO NOT keep the Linux-style file permissions.

This can cause problems. Indeed, one problem is that MS does not support symbolic links.

Do as *ajgreeny* suggested.. 
reformat the USB into something that will support Linux file systems.
And for those that say that a vFAT is needed for Windows compatibility,
I ask "Of what use is a Linux /home backup to a Windows system?" :) 
USB drives are cheap enough to be dedicated to one task.

Backing up a Linux File System to a Microsoft File System does not allow ALL the information/meta-information to be copied.
*Is this want you want in a back-up?*

> When I tried this, **I get the error that Symbolic links cannot be created**.


"We rest our case"

---

### Post by dadgetboy on 2010-04-15
I recommend booting a LiveCD, and running 
```
gksudo nautilus
```

then, just use the GUI to mount the correct volume, and copy it to the usb flash drive.

---

### Post by ajgreeny on 2010-04-16
> **dadgetboy said:**
> I recommend booting a LiveCD, and running 
```
gksudo nautilus
```then, just use the GUI to mount the correct volume, and copy it to the usb flash drive.
That's a strange way to do a simple task, surely?  Why bother rebooting to a live CD when you can do it all with rsync, or if you prefer, grsync with a nice GUI.

The main problem, I still think, is the file system you are copying to; it needs to accept linux permissions for a foolproof backup of all your /home contents.

---

### Post by dcstar on 2010-04-17
> **ajgreeny said:**
> 
........
The main problem, I still think, is the file system you are copying to; it needs to accept linux permissions for a foolproof backup of all your /home contents.

Simply put the entire contents of /home into a tar file and then copy that to anything.

All the file attributes will be preserved inside the tar file.

---

### Post by chris.jericho on 2010-04-17
yeah that would be a better way to actually do it.

---

### Post by ajgreeny on 2010-04-17
> **dcstar said:**
> Simply put the entire contents of /home into a tar file and then copy that to anything.

All the file attributes will be preserved inside the tar file.
Good thinking dcstar!  A great way to overcome the permissions problem.

I still prefer to use rsync and do the backups much quicker, and of course, not waste time and space with files I already have backed up previously.

---

