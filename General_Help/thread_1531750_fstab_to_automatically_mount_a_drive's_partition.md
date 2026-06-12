---
title: "fstab to automatically mount a drive's partition"
date: 2010-07-15
forum: General Help
---

### Post by Tom_ZeCat on 2010-07-15
I edited my fstab file in /etc attempted to get Ubuntu to automatically mount a hard drive's partition on startup.  However, the result was the drive not only didn't mount; it became unmountable.  If I tried to mount it by clicking on it with the File Browser, I got an error message saying the drive cannot be mounted.  I've reverted to my previous version of my fstab file.  Now I can at least mount it if I click on it.  

Obviously, I've done something wrong.  In Gparted, the partition is designated as "/dev/sdb5."  In the File Browser, it's called "/media/Win XP."  It's an 80 gig partition on the PC's 1 TB internal secondary drive.  Windows XP is installed on it.  Windows 7 is installed on the 950 gig other partition.  Ubuntu is not on it.  Ubuntu is on the primary 250 gig drive.  

Here's my fstab file as I edited it.  The added line is in blue.  

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fc5ba8bc-1b72-4e1c-9f8c-03825b46ce8b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=fd1cd99a-b7f8-46da-b777-b57c34e566b7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[COLOR="Blue"]/dev/sdb5 /media/Win\ XP ntfs-3g defaults 0 0[/COLOR]

I want this 80 gig partition to automatically mount because I've written a program that needs to automatically save a file to it when Ubuntu boots up.  The program crashes if the drive isn't mounted.  My other option besides an fstab-based auto-mount is to program a mounting in.  It could run a terminal command to mount it, but it seems simpler to use fstab if I can get it to work.

---

### Post by cj.surrusco on 2010-07-15
I would erase the line in the fstab and try using the NTFS Configuration Tool (available in the Software Center), which will allow you to easily set NTFS drives to auto-mount.

---

### Post by 98cwitr on 2010-07-15
there's a gui for this in the software center...just search ntfs and it's first on the list.

---

### Post by Morbius1 on 2010-07-15
I don't see anything wrong with your fstab entry:
>  [COLOR=Blue]/dev/sdb5 /media/Win\ XP ntfs-3g defaults 0 0[/COLOR]                      Assuming there really is a "/media/Win XP" directory. I usually prefer to use \040 explicitly :
```
 [COLOR=Blue]/dev/sdb5 /media/Win\040XP ntfs-3g defaults 0 0[/COLOR]
```But your way should work.

Post the output of the following command just to check on sdb5:
```
sudo blkid -c /dev/null
```

---

### Post by Tom_ZeCat on 2010-07-15
> **Morbius1 said:**
> I don't see anything wrong with your fstab entry:
Assuming there really is a "/media/Win XP" directory. I usually prefer to use \040 explicitly :
```
 [COLOR=Blue]/dev/sdb5 /media/Win\040XP ntfs-3g defaults 0 0[/COLOR]
```But your way should work.

Post the output of the following command just to check on sdb5:
```
sudo blkid -c /dev/null
```

It worked!  Adding the "\040" did the trick.  Fstab must not have liked the spacer the way I had it.  I didn't know about \040 for spacers.  Gonna save that in my bag of tricks.  

Looks like I won't be needing the NTFS configuration tool, but thanks for telling me about it just the same.  Now I know of its existence and it too will therefore go into my bag of tricks.

---

### Post by Morbius1 on 2010-07-16
A cautionary note about the app called mountmanager - it's a destructive utility in that it doesn't edit fstab it replaces it. Make a backup of your current fstab before you install it. I installed it recently just to see why everyone was recommending it and it ended up deleting some of my own entries. Specifically it deleted the following line:
> bindfs#/DATA /home/Shared fuse perms=0666:+x 0 0Mountmanager must have looked at that and said "what the @!%& is that" and poof - away it went. 

I don't much care for ntfs-config either. The first thing it asks you when you initially run it is if you want to enable write support for ntfs partitions.  Write support for NTFS partitions have been enabled by default since I think Hardy so I'm not sure why it didn't know that and I'm not sure what it does when you answer Yes.

Sorry for the rant. You can probably tell I'm somewhat "old school" when it comes to things like this :lol:

---

