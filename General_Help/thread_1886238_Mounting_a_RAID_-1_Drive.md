---
title: "Mounting a RAID -1 Drive"
date: 2011-11-24
forum: General Help
---

### Post by stonegrey on 2011-11-24
Evening all.

I'm trying to get a RAID-1 1TB hard drive to automount after startup. I have 2 drives in the PC, one of 80GB running Ubuntu 11.04 and the other was out of my WD Mybook world, it has about 450GB's of music etc that i don't want to accidentally corrupt or erase by doing things i don't understand.

I've set up MDADM - i think, and a SAMBA share as i want to use this PC as a mini home server.

I can mount the drive quite easily by going into Disk utility, but this will be difficult if i don't have a monitor or keyboard attached!

thanks in advance for any help getting this drive to mount automatically.

PS can it be done through GNOME?

---

### Post by ptrakk on 2011-11-24
I would set up tightvnc on that server. also you might have to edit your /etc/fstab to mount that drive automatically. gparted is useful too.

---

### Post by stonegrey on 2011-11-24
> **ptrakk said:**
> I would set up tightvnc on that server. also you might have to edit your /etc/fstab to mount that drive automatically. gparted is useful too.

OK, what do i need to put in /etc/fstab to get it to automount?

the output of mdadm:

>  ~$ sudo mdadm -D /dev/md4
/dev/md4:
        Version : 0.90
  Creation Time : Sat Jun 14 03:51:21 2008
     Raid Level : raid1
     Array Size : 972703552 (927.64 GiB 996.05 GB)
  Used Dev Size : 972703552 (927.64 GiB 996.05 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 4
    Persistence : Superblock is persistent

    Update Time : Thu Nov 24 19:53:26 2011
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : c4dd7a76:03b151dc:6ec0c337:d14e8417
         Events : 0.225714

    Number   Major   Minor   RaidDevice State
       0       8       20        0      active sync   /dev/sdb4
       1       0        0        1      removed
 fstab looks like this:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fe293a61-5048-4a6a-be01-af4e89faca5b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=78f50e64-b56d-4036-af6e-0a80ecb0ae18 none            swap    sw              0       0

it's 11.04 desktop i'm running not server, just in case there is any difference in commands etc.

---

### Post by DeonS on 2011-11-25
Hi Stonegrey.

Could you please run the following command and post the output.

    cat /proc/mdstat
    
I have an article on linux software raid that might be on use to you as well.

[http://www.deonsworld.za.net/2011/11/26/managing-linux-software-raid/](http://www.deonsworld.za.net/2011/11/26/managing-linux-software-raid/)

---

### Post by stonegrey on 2011-11-26
i figured it out in the end, i was mounting it as a drive not as raid. once i set out fstb in full screen, i could see how it works.  

thanks to those who have posted.

---

