---
title: "Unable to mount usb stick in thunar"
date: 2010-01-06
forum: General Help
---

### Post by decomp on 2010-01-06
Hi all,

I'm unable to mount external drives in thunar. Pcmanfm works fine. Ive tried a 2gb usb stick and a sd card reader. both give the same error. I used to be able to mount drives with thunar. What happened? I'm using ubuntu 9.10, installed lxde on top of server edition. Thunar is 1.0.1 , from the repos. Here is the output from the usb stick:


Failed to mount "2G Removable Volume".
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,        missing codepage or helper program, or other error        In some cases useful info is found in syslog - try        dmesg | tail  or so  .

---

### Post by Who on 2010-02-15
I have the same problem and I made my system using rootstock (it's on ARM)

---

### Post by picklemonkey on 2010-02-26
I'm also having the same problem.  Does anybody have any ideas for troubleshooting USB flash stick mounts?

---

### Post by ubunterooster on 2010-02-26
not a rare problem ;'(

my alternative until I find solution: Icewm

---

### Post by NefariousNobo on 2010-02-26
Personally, I prefer Nautilus :P

That being said, you could always try the "mount" command. Usually, I find it gives me better errors when it doesn't work than a file manager does. However, mount almost always works.

Good luck...

---

### Post by ubunterooster on 2010-02-26
If you mount from the command line, YOU MUST unmount from command line also. I lost some mp3's I had not yet backedup this way. "it's not writing, i can just pull it out"

---

### Post by picklemonkey on 2010-02-27
I found a solution to my problem in these two threads:

[http://ubuntuforums.org/archive/index.php/t-979893.html](http://ubuntuforums.org/archive/index.php/t-979893.html)
[http://forum.eeeuser.com/viewtopic.php?pid=354743](http://forum.eeeuser.com/viewtopic.php?pid=354743)


I went into /etc/fstab and commented out the last 3 lines.  I knew that I only had a sda and sdb mount, and had never seen a sdc or sdd mount in the past.  I went to the /media/sdc1, sdc2, and sdd1 folders, confirmed that they were empty, then commented them out and reboot.  I'm now able to mount my USB stick AND my Google Nexus One phone (my issue [here](http://ubuntuforums.org/showthread.php?t=1400341))!

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                                    0  0  
# / was on /dev/sda6 during installation
UUID=674a9264-7eb3-4f2d-a178-e0be7163d574  /               ext3         relatime,errors=remount-ro                  0  1  
# swap was on /dev/sda7 during installation
UUID=aa239c6a-f90c-46b7-8860-e0e368a50f5f  none            swap         sw                                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8                       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8                    0  0  
/dev/sdb1                                  /media/sdb1     ntfs         defaults,users,utf8,mark=007,uid=1000       0  0  
# /dev/sda5                                  /media/sda5     vfat         defaults,users,umask=000                            0  0  
/dev/sda5                                  /media/sda5     vfat         defaults,users,utf8,umask=007,uid=1000      0  0  
#### /dev/sdc1                                  /media/sdc1     vfat         defaults,users,utf8,mark=007,uid=1000,user  0  0  
#### /dev/sdc2                                  /media/sdc2     hfsplus      defaults,users,utf8,mark=007,uid=1000,user  0  0  
#### /dev/sdd1                                  /media/sdd1     ntfs         defaults                                    0  0  
```

---

