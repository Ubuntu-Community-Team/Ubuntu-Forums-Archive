---
title: "How to resize a partition"
date: 2010-09-30
forum: General Help
---

### Post by satimis on 2010-09-30
Hi folks,

Ubuntu 10.04 64-bit (installed on installer)

What will be an easy and safe way to resize partition?  Boot up the LiveCD?  Or can I run
resize2fs on Ubuntu while the latter is running?

$ sudo fdisk -l```


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d09a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c92e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3648    29295616   83  Linux
/dev/sdb2            3648        5593    15624193    5  Extended
/dev/sdb3            5593       29908   195312640   83  Linux
/dev/sdb4           29908      121602   736527360   83  Linux
/dev/sdb5            3648        5593    15624192   82  Linux swap / Solaris

```

Partition of the HD:-
/dev/sdb1	/root
/dev/sdb3	/home
/dev/sdb4	/kvm

This is a newly installed box without files on /kvm.  Now I want to resize /home taking up the complete capacity of /kvm which will be removed/deleted.

Pls advise.  TIA

B.R.
satimis

---

### Post by woodmaster on 2010-10-01
***NOTE***

Backup first.

***********

Then boot live cd and resize from gparted(or other partitioning tool) there.  The partition must be unmounted to edit it.

---

### Post by oldfred on 2010-10-01
With sdb4 next to sdb3 you should be able to easily expand your /home.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

You could convert sdb4 to a data partition separate from /home and either mount it in /home in fstab or mount it and link folders into /home.

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by satimis on 2010-10-01
> **woodmaster said:**
> ***NOTE***

Backup first.

***********

Then boot live cd and resize from gparted(or other partitioning tool) there.  The partition must be unmounted to edit it.

Thanks

satimis

---

### Post by satimis on 2010-10-01
> **oldfred said:**
> With sdb4 next to sdb3 you should be able to easily expand your /home.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


Hi,

Thanks for your advice.  So I still need resizing the partition while the OS is NOT running?

I think gparted is on Ubuntu LiveCD?

> 
You could convert sdb4 to a data partition separate from /home and either mount it in /home in fstab or mount it and link folders into /home.


Could you pls explain in more detail.  Whether sym-link /kvm to /home permanently?  How to do it so the link won't be gone in next reboot?

$ cat /etc/fstab ```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5336d7f0-1a0d-4f37-b7d4-56b949ec03f7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=415bba81-2cfb-4f2a-92ba-3128141e3a00 /home           ext4    defaults        0       2
# /kvm was on /dev/sda4 during installation
UUID=d3d5adde-4ad4-43c0-8d26-967c84ee583e /kvm            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f99198b1-2fc5-443f-b78d-bb9b0be13df5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

My intention creating /kvm is for storage of the guest images.  Later I found it is NOT convenient, better retaining them on /home

B.R.
satimis

---

### Post by oldfred on 2010-10-01
It looks like you already have an entry in fstab, but you are mounting it into root. I am not sure if defaults will give you full ownership and permissions since it is mounted in root.

See my links in previous post explaining the fstab entry, ownership, permissions and linking. I have folder in my /data partition and link each folder. I have not had any issues with links after a reboot. I also saved my entries from history and copied them into a bash script to rerun on new installs. 

You cannot modify partitions that are mounted, so it is best to use liveCD (although you may still have to swapoff). gparted is on Ubuntu liveCD or can be downloaded as a separate liveCD.

---

