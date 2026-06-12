---
title: "ubuntu 9.10 partition mount problems"
date: 2010-03-15
forum: General Help
---

### Post by captainanarchist on 2010-03-15
Hi, I've made a new partition called "Seneca-HD" and it's sda5. I went to the terminal as sudo and typed **mount** **/dev/sda5** and **mount /media/Seneca-HD**

mount /dev/sda5         gave me the following error:
mount: can't find /dev/sda5 in /etc/fstab or /etc/mtab

mount /media/Seneca-HD        gave me the following error:
mount: can't find /media/Seneca-HD in /etc/fstab or /etc/mtab

I really appreciate any help on this and thanks in advance. Also If you can please feel free to provide me links / readings or explanation of what's happening here and what is fstab mtab and fdisk. I love linux and Ubuntu even more and would love to learn what's going on here.


**#sudo fdisk -l** 


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1eec587

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9119    73248336   83  Linux
/dev/sda2            9120       19457    83039985    5  Extended
/dev/sda5            9120       19096    80140189+   c  W95 FAT32 (LBA)
/dev/sda6           19097       19457     2899701   82  Linux swap / Solaris

Disk /dev/sdb: 3959 MB, 3959422976 bytes
122 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 7564 * 512 = 3872768 bytes
Disk identifier: 0x000f1802

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1022     3865173    c  W95 FAT32 (LBA)

[B]
/etc/fstab[/B] contents: 

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=609b4bac-f35a-423a-838f-8b6670841e14 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=79f88889-6468-43a3-ba9a-fd8fbeef6178 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

**/etc/mtab **contents:

/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ahmad/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ahmad 0 0
/dev/sdb1 /media/AHMAD-SD vfat rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0

---

### Post by zvacet on 2010-03-15
Try [this.]("http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm")

---

### Post by pastalavista on 2010-03-15
You need to use sudo before every administrative command so it knows you are doing it as root. Try this ```
sudo mount /dev/sda5 /media/Seneca-HD
```

---

### Post by captainanarchist on 2010-03-16
ty for the replies, i was sudo (using custom application with start up as sudo).

i figured out the problem, turns out i wasn't specifying where i would like to mount sda5

so 

sudo mount /dev/sda5 /media/cdrom 

worked perfectly :)

---

