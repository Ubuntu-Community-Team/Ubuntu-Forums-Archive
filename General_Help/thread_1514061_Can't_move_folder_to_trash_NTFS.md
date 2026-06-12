---
title: "Can't move folder to trash NTFS"
date: 2010-06-20
forum: General Help
---

### Post by Zortrox on 2010-06-20
I have an NTFS partition automatically mounted in fstab.  I have read many forums and have done what they have to try and fix this problem, but it still won't move the files to the NTFS trash folder.  What can I do to make this work?

Here is my fstab entry:

```
# NTFS partition /dev/sda1
UUID=5D924B8408514F71 /media/MediaDrive             ntfs    rw,auto,users,nosuid,uid=1000,fmask=137,dmask=027,utf8         0       0
```

---

### Post by Zortrox on 2010-06-20
These are the things that I tried:  I added the option uid=1000.  I also added fmask and dmask options.  By the way, I AM user 1000.  I put the id command in terminal.  Thanks in advance for the help!

---

### Post by MaikoID on 2010-07-14
I have the same problem, I can't move my files to trash, I have two partitions: NTFS and FAT32

my fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=55180fef-016c-4489-b485-7bcda07a1f12 /               ext4    errors=remount-ro 0       1
# /media/Files was on /dev/sda5 during installation
UUID=9824-3D4E  /media/Files    vfat    utf8,umask=007,gid=46 0       1
# /media/Windows was on /dev/sda2 during installation
UUID=86C0FE36C0FE2BD5 /media/Windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /mnt/NTFS_ was on /dev/sda1 during installation
UUID=8ADC7AB8DC7A9E5F /mnt/NTFS_      ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=f8ee4ceb-35f4-453f-8064-cdcdf08968d6 none            swap    sw              0       0

```
What can I do ? I've tried everything but I can't fix it.

Bye

---

### Post by m4tic on 2010-07-14
> **Zortrox said:**
> I have an NTFS partition automatically mounted in fstab. I have read many forums and have done what they have to try and fix this problem, but it still won't move the files to the NTFS trash folder. What can I do to make this work?
 
Here is my fstab entry:
 
```
# NTFS partition /dev/sda1
UUID=5D924B8408514F71 /media/MediaDrive             ntfs    rw,auto,users,nosuid,uid=1000,fmask=137,dmask=027,utf8         0       0
```
 
Now that's a complicated setup in the options field. May i ask why didn't you just stick to "defaults"?

---

### Post by m4tic on 2010-07-14
edit: Try installing mountmanager. Everything is easy if you let it take over. Ntfs-config is also great, i used it back when i was in 8.04 and also pysdm
 
[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)
[COLOR=#0e774a][http://flomertens.free.fr/**ntfs**-**config**/]("http://flomertens.free.fr/ntfs-config/")[/COLOR]
[COLOR=#0e774a]_[COLOR=#810081][http://linux.softpedia.com/get/System/System-Administration/MountManager-35972.shtml](http://linux.softpedia.com/get/System/System-Administration/MountManager-35972.shtml)[/COLOR]_[]("http://flomertens.free.fr/ntfs-config/")[/COLOR]

---

### Post by langmarp on 2010-08-11
[http://ubuntuforums.org/showthread.php?t=1499345](http://ubuntuforums.org/showthread.php?t=1499345)

this works for me

---

