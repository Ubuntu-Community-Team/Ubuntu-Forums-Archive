---
title: "Unable to mount Hard Drive &lt;--- (That's the name of my external)"
date: 2010-09-28
forum: General Help
---

### Post by chrismonster16 on 2010-09-28
I just installed pysdm so I could configure what drives mount on boot, and now when I go to access my external harddrive, this is what I get:
**Unable to mount Hard Drive**
Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 11 in /etc/fstab is bad
[mntent]: line 12 in /etc/fstab is bad
[mntent]: line 13 in /etc/fstab is bad
[mntent]: line 14 in /etc/fstab is bad
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab


Please help. I need to access my hard drive

---

### Post by mikewhatever on 2010-09-28
Please post the outputs of the following commands:

sudo fdisk -l

cat /etc/fstab

---

### Post by chrismonster16 on 2010-09-29
Here it is:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       54382   436821164    1  FAT12
/dev/sda2           59334       59551     1746945    5  Extended
/dev/sda3           59552       60801    10040625    7  HPFS/NTFS
/dev/sda4           54382       59334    39773184   83  Linux
/dev/sda5           59334       59551     1746944   82  Linux swap / Solaris

Partition table entries are not in disk order

And then the second one:

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97666212

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc              proc  nodev,noexec,nosuid         0  0  
# / was on /dev/sda4 during installation
UUID=878a044c-1065-4814-b6f1-2b0967ce0047  /                  ext4  errors=remount-ro           0  1  
/dev/sdb1                                  /media/Local Disk  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sdb1                                  /media/Local Disk  ntfs  defaults             0  0  
/dev/sdb1                                  /media/Local Disk  ntfs  defaults             0  0  
/dev/sdb1                                  /media/Local Disk  ntfs  nls=iso8859-1,ro,umask=000  0  0  

Please tell me you can help me, lol. I'm new to Ubuntu and I love it. I just need to get a better insight on how things work haha

---

### Post by chrismonster16 on 2010-09-30
Please help me. I need to access my external hardrive. My Windows 7 partion crashed last night and I need to access my external drive so I can get my Windows 7 recovery so I can use Windows again.:P

---

### Post by msakms on 2010-09-30
Try installing "Disk utility" from ubuntu software manager and see if your hard is healthy "or not" and do a repair if necessary.

---

### Post by chrismonster16 on 2010-09-30
I checked. It says it's healthy. Idk what to do. Any other suggestions?

---

### Post by ddonohu2 on 2010-09-30
I'm no expert and I've never used psydm so you may want to wait for someone more experienced. For what it's worth here's my opinion.

If you're going to do any of this I recommend making a backup of the file "/etc/fstab".

It looks to me like pysdm has written bad lines to your fstab. To start with you might want to uninstall pysdm, next, open your fstab (by opening a terminal and typing "gksu gedit /etc/fstab") you will see a copy of one of the documents you pasted earlier. Your fstab is responsible for mounting options (it stands for filesystem table or something...). If you remove the last four lines of your fstab (the ones starting "/dev/sdb1") and save and exit gedit then you should be able to manually mount your partition. If you still want to set up automount options for you partition then you should read this:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Editing fstab yourself is easier than it looks since most of the time the default options are good enough.

---

### Post by chrismonster16 on 2010-09-30
[@ddonohu2]("http://ubuntuforums.org/member.php?u=941980"), I have to thank you. That worked like a charm. Thank you!

---

