---
title: "Ubuntu won't open my USB flash drive"
date: 2010-06-29
forum: General Help
---

### Post by blackbird09 on 2010-06-29
I keep getting an error message saying "The volume uses the FAT 32 file system which is not supported by your system." 
I've formatted the drive a few times and the problem remains, but only with this one. What should I do? [IMG]http://gallery.bloodyravens.co.cc/album/errormessage.jpg[/IMG]
edit: I have tried formatting it to other formats, Ext3, fat 16, etc. but the error message stays the same.

---

### Post by kalistona on 2010-06-29
nothing.
you restart your computer and you go to system - administration - utilitaire de disques..
(ok you understand even in french, i hope so !)
you see your disk ! is it bootable ? has it a name ?

sometimes ubuntu does not accept usb/key (multimedia).

you can go also on windows if you are in dual boot and give a name and 'repare errors'...

sometimes you do not see it on the desktop, it does not mean nothing.  
maybe ubuntu do not understand why you format a key wihout install an O.S ?

---

### Post by dino99 on 2010-06-29
format this stick with gparted or partedmagic (why fat32 , so oldish ?)

---

### Post by blackbird09 on 2010-06-29
The problem is that this has been going on for weeks now, every other flash drive works but mine. It doesn't show up on desktop, and when I format it or repair the errors on windows the problem stays.

---

### Post by blackbird09 on 2010-06-29
It's not in fat32, currently its in ext2, the computer only reads it as fat32 so I can't change anything to fix it. :| I've formatted it three times on GParted to no avail..

---

### Post by supergrav on 2010-06-29
> **blackbird09 said:**
> It's not in fat32, currently its in ext2, the computer only reads it as fat32 so I can't change anything to fix it. :| I've formatted it three times on GParted to no avail..

Check if there is an entry for your usb stick in /etc/fstab file.

---

### Post by blackbird09 on 2010-06-29
how do I find out which one is which? there's three in there. 
# /dev/sda1
# /dev/sda5
/dev/scd0
No, it's not in there. only Swap file, hard drive and the CD drive. How can I fix this?

---

### Post by kalistona on 2010-06-29
ok : go to windows ! 
parameters then system them my disks (do not choose your ntfs !)click right option empty 
see your disk and erase it (your usb ) now it is empty : format it it is a[COLOR=Blue] new key[/COLOR] now.

---

### Post by supergrav on 2010-06-29
> **blackbird09 said:**
> how do I find out which one is which? there's three in there. 
# /dev/sda1
# /dev/sda5
/dev/scd0

If there are only those three, probably there isn't any entry.
Have you tried mounting it manually?

---

### Post by blackbird09 on 2010-06-29
How do I mount it manually? I saw a thread with it in it awhile ago but I lost it.

---

### Post by supergrav on 2010-06-29
> **blackbird09 said:**
> How do I mount it manually? I saw a thread with it in it awhile ago but I lost it.

Use sudo mount -t vfat /dev/sdx "directory", your device name can be found in folder /dev and "directory" is a path name where your usb stick will be mounted.

---

### Post by blackbird09 on 2010-06-29
I keep getting the > mount: can't find /dev/sdb/ in /etc/fstab or /etc/mtab
 error while trying

---

### Post by supergrav on 2010-06-29
Are you sure that your device is /dev/sdb? Is there "sdb" entry in /dev folder while you try this?

---

### Post by blackbird09 on 2010-06-29
yes, and when I unplug the flash drive it's the only file to disappear, when plugging it in it's the only one that appears.

---

