---
title: "mount point for cdrom?"
date: 2011-05-27
forum: General Help
---

### Post by daniel.cotter on 2011-05-27
I am trying to add my natty Live Cd as a repository, by issuing apt-cdrom add, but even autodetecting the mount point fails.

```
apt-cdrom --auto-detect add

```  How do I determine the mount point for the cdrom in order to tell apt-cdrom where to look?

Output:

```
Using CD-ROM mount point /media/apt/
Identifying.. 
E: Unable to stat the mount point /media/Ubuntu\04011.04\040amd64/ - stat (2: No such file or directory)
E: Unable to stat the mount point /media/apt/ - stat (2: No such file or directory)
W: Failed to mount '/dev/sr0' to '/media/apt/'
E: Unable to change to /media/apt/ - chdir (2: No such file or directory)
E: Unable to stat the mount point /media/Ubuntu\04011.04\040amd64/ - stat (2: No such file or directory)

```Any clues?

---

### Post by doas777 on 2011-05-27
well, the device should mount to /media/cdrom0, but if you have more than one, you will have to determine which drive has teh lower busid to figure out which one will mount to 0. subsequent cd drives will mount to /media/cdromX where X is a zero-based integer.

---

### Post by lordadi on 2011-05-27
I *think * cdroms are mounted to /media/cdrom or /media/cdrom0, so maybe you need to tell it to look there?

---

### Post by daniel.cotter on 2011-05-27
I tried to add the line into etc/fstab (as root) and still get the same error.  I am not clear on the exact format for the line, so I guessed a couple different ways.  No change to the error message after each edit.  Here is my fstab, restored to its original contents:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b1cfd664-0167-45c0-804b-cc98b821e265 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4999abfa-969f-4959-b9ab-e9b1fbc57524 none            swap    sw              0       0
```

If any of you can tell me the correct format, I will try that.  Or, if I am approaching this wrong, I'm listening.

Thanks for the answers

---

### Post by mc4man on 2011-05-27
If you wanted a static mount for your cd/dvd drive then typically - 
first make sure a mount dir. exists, if not create
```
sudo mkdir /media/cdrom0
```

in fstab a new line - assumes device is /dev/sr0
```
/dev/sr0   /media/cdrom0   udf,iso9660 user,noauto,exec   0 0 
```

( The default now for cd/dvd drives is no fstab, mounts to /media/volume_label dynamically (mount dir. is auto created when disk is inserted, deleted when disk is removed

Edit: if after creating above ect. you might try creating a link in /media named cdrom that points to /media/cdrom0

---

### Post by lordadi on 2011-05-28
If you are trying to create a mountpoint for a disk, (an iso you have burnt) - you can typically just mount the iso itself. For this I use gmount-iso.

Not sure if this applies to your situation but thought I would pass it along. Be wary though, if you are trying to upgrade with the Natty disk, you probably should use a physical disk (so that packages remain available, in case /home is unmounted).

---

