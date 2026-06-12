---
title: "Cannot move file to trash, do you want to delete immediately?"
date: 2010-03-07
forum: General Help
---

### Post by DrJohn999 on 2010-03-07
Karmic Desktop, was upgraded from Jaunty
This behavior, arguably bug, has been around for a long time (at least since Hardy). After reading thru forums etc I thought it would be an easy fix, but not so.

Problem: deleting a file via Nautilus from an NTFS-3G drive mounted as fuseblk gives:

```
Cannot move file to trash, do you want to delete immediately? 
The file "<filename>" cannot be moved to the trash. 
[Cancel][Skip][Delete]
```

A solution that crops up in many places is to add 'uid=1000,gid=1000' to the drive's automount line in fstab, then create a /.Trash-1000 on the drive's root mountpoint. My uid is 1000, but this doesn't work on my system; after changing fstab and remounting / rebooting the same "Cannot move..." message appears upon delete.

Here's the relevant line from fstab:
```
UUID=1C009CAA2D79EFE5	/media/shared0	ntfs-3g,uid=1000,gid=1000,auto,exec	0  2

```
and:
```
$ df -T
/dev/sdd1  fuseblk   732572000 447410568 285161432  62% /media/shared0
```
The drive permissions read as, for example,
```
127198 0 drwxrwxrwx 1 root root    0 2010-03-07 10:19 .Trash-1000

```
not unexpectedly as it's ntfs.

Am I missing something in the mount arguments? Thanks!

---

### Post by dcstar on 2010-03-07
> **DrJohn999 said:**
> Karmic Desktop, was upgraded from Jaunty
This behavior, arguably bug, has been around for a long time (at least since Hardy). After reading thru forums etc I thought it would be an easy fix, but not so.

Problem: deleting a file via Nautilus from an NTFS-3G drive mounted as fuseblk gives:

```
Cannot move file to trash, do you want to delete immediately? 
The file "<filename>" cannot be moved to the trash. 
[Cancel][Skip][Delete]
```

A solution that crops up in many places is to add 'uid=1000,gid=1000' to the drive's automount line in fstab, then create a /.Trash-1000 on the drive's root mountpoint. My uid is 1000, but this doesn't work on my system; after changing fstab and remounting / rebooting the same "Cannot move..." message appears upon delete.
........

NTFS does **not** support all Linux filesystem requirements, you **cannot** have all the features of Linux systems using NTFS.

NTFS **cannot** have file/folder names starting with "."

There is no "bug", it is the inappropriate use of a foreign filesystem on a Linux system.

---

### Post by mister_playboy on 2010-03-07
> **dcstar said:**
> NTFS does **not** support all Linux filesystem requirements, you **cannot** have all the features of Linux systems using NTFS.

What he said... :)

---

### Post by spoketire on 2010-05-18
You can do this on ntfs drives in linux, but not if theyr'e automounted. I have one ntfs drive that I use for file storage, and when I have it automounting, it has this problem. I have another ntfs partition that is for windows, which I haven't automounted, and I can move files to the trash on that partition without any problems. I have been using the fstab method of automounting. There has to be a way to fix this.

---

### Post by langmarp on 2010-08-11
[http://ubuntuforums.org/showthread.php?t=1499345](http://ubuntuforums.org/showthread.php?t=1499345)

this works for me

---

### Post by spoketire on 2010-08-11
Thanks, I will give it a try.

---

### Post by cengelbrecht on 2011-03-01
> **dcstar said:**
> NTFS does **not** support all Linux filesystem requirements, you **cannot** have all the features of Linux systems using NTFS.

NTFS **cannot** have file/folder names starting with "."

There is no "bug", it is the inappropriate use of a foreign filesystem on a Linux system.


This is nonsense. NTFS supports files and folders starting with a dot, and the recycle bin (from Windows) and the trash can (from Nautilus) works perfectly if you mount the NTFS drive from user space.

The problems described come in if you automount NTFS volumes using ntfs-3g.

---

### Post by _Impact_ on 2011-04-22
This is what worked for me on my Ubuntu 10.10:

This is how it was before:

```
/dev/sda7                                  /media/MiSAFE  ntfs  defaults         0  0  
```

This is what it is now:

```
/dev/sda7                                  /media/MiSAFE  ntfs  defaults,uid=1000,gid=46,locale=en_US.UTF-8         0  0  
```

To get the gid, go to terminal and type
```
cat /etc/group
```

find the line with 

```
plugdev:x:46:USERNAME
```

there's the gid

reboot and done!

---

### Post by FrAggLE-Rock on 2011-08-29
> **_Impact_ said:**
> This is what worked for me on my Ubuntu 10.10:

This is how it was before:

```
/dev/sda7                                  /media/MiSAFE  ntfs  defaults         0  0  
```This is what it is now:

```
/dev/sda7                                  /media/MiSAFE  ntfs  defaults,uid=1000,gid=46,locale=en_US.UTF-8         0  0  
```To get the gid, go to terminal and type
```
cat /etc/group
```find the line with 

```
plugdev:x:46:USERNAME
```there's the gid

reboot and done!


worked for me too in natty thx, 

i was looking for a solution for quiet a time now.

---

### Post by DrJohn999 on 2011-08-29
I eventually changed to ext4 for this drive. I run daily backups, from a 10.04 LTS server, so it was easy to remove the ntfs partition, create an ext4 partition, and restore the contents with file attributes (owner, permissions, dates, etc) intact.

The new partition worked well for me, with functional trash, until I upgraded to Natty (11.04). From then on, Nautilus resumed the "Cannot move file to trash..." behavior. A solution for this can be found here: [http://ubuntuforums.org/showthread.php?t=1810964](http://ubuntuforums.org/showthread.php?t=1810964)

I originally had the ntfs partition as a legacy from the (not so) good old days of Windows XP. When migrating to Ubuntu, I originally configured for dual boot and so needed the ntfs partition to get access from both worlds. Later, I moved XP into a VirtualBox VM under 10.10. I moved the files into ext4 and shared the partition via VirtualBox. Same thing for a Windows 7 VM. Neither of the Windows VMs has trash for the shared drive, so it's a reversal of function, but I use Windows so seldom now that it really doesn't matter.

At some point I'll try mounting the ext4 partition in an Ubuntu VM with NFS. In theory this should work with Nautilus' trash functionality in the VM as long as /.Trash-<uid> can be created or is present. However, this makes for a potential cross-machine uid conflict, so maybe it won't work...

---

