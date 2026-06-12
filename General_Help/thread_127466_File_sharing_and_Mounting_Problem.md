---
title: "File sharing and Mounting Problem"
date: 2006-02-09
forum: General Help
---

### Post by aseem_mal on 2006-02-09
I just finished a dual boot - Win XP + Ubuntu

This is my file system:
> 
aseem@Goobuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4             6.4G  1.7G  4.4G  27% /
tmpfs                 443M     0  443M   0% /dev/shm
tmpfs                 443M   13M  431M   3% /lib/modules/2.6.12-9-386/volatile
/dev/hda5             1.8G   35M  1.7G   3% /home
/dev/hda1              15G  2.4G   13G  16% /media/hda1
/dev/hda6              31G   16K   31G   1% /windows


I am not able to access the Fat 32 partition from Ubuntu. Its not even mounted. What can i do to mount it, and have write access to it?:confused: 

Thanks,
A

---

### Post by aysiu on 2006-02-09
See the fourth link of my signature.

---

### Post by aseem_mal on 2006-02-09
> **aysiu]See the fourth link of my signature.[/QUOTE]

Hi. I did exactly as in your fourth link in the signature. But when I try to put a file into the newly mounted partition, it doesn said:**
> 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda6       /windows        vfat    defaults        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0




Please help. :(

---

### Post by cotcot on 2006-02-09
Your fstab is showing "defaults" on the line for ntfs and vfat. This looks like your old fstab. There should be "umask=0222" for the ntfs and "umask=000" for the vfat. Please compare you fstab with the fourth link of aysiu.
Then you will still not be able to write to the ntfs as this is not recommended (possible but not guaranteed stable). Writing to the vfat is possible as long as the file is not longer than 4GB. 
Nice to know : you can see ext2 partition from XP if you install the XP driver for it : see [www.fs-driver.org](www.fs-driver.org).

---

### Post by moTaro on 2006-02-10
Put this in your /etc/fstab and you will be able to write to your Windows FAT partition.

> 
/dev/hda6	/windows    vfat    iocharset=utf8,umask=000 0   0


---

