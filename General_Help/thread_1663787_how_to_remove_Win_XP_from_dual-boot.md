---
title: "how to remove Win XP from dual-boot"
date: 2011-01-10
forum: General Help
---

### Post by kokoshmusun on 2011-01-10
Hi, 
  I'd like to remove Win XP from my dual-boot.  I've searched and haven't found a straightforward answer. If re-installing ubuntu has advantages, I'm willing to do that, but if there's an easier way, maybe someone can point me toward it. 
  Many thanks!

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x567de008

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19760   158722168+   7  HPFS/NTFS
/dev/sda2           19761       40314   165095378    7  HPFS/NTFS
/dev/sda3           40314       60802   164568065    5  Extended
/dev/sda5           40314       60050   158532608   83  Linux
/dev/sda6           60051       60802     6034432   82  Linux swap / Solaris


---

### Post by sanderd17 on 2011-01-10
First of all: DO A BACKUP. if only a little thing goes wrong in the next steps, your data could be lost.

To get rid of win XP: boot up a live cd (or a live USB), open gparted (I believe  it is already installed, if not, install it) and delete the partitions sda1 and sda2. I suppose those are the C and D partition of windows since they are formatted as NTFS.


I allways keep another partition for Linux. Currenlty I use Mint 10 and I have Ubuntu 10.10 on an other partition. If I want to install a new distro or update it, I install it on the partition where the Ubuntu 10.10 is and see if it works. If it works, I put all my data from the mint to ubuntu. That way I always have a 'backup' distro. If you want that, just create a new partition and install ubuntu (or something else) on that partition.

If you want more space for the current Ubuntu that you're running. Then you should do the following: you now have 2 ext partitions I think that sda5 and sda6 are inside sda3. So you have to enlarge sda3 and sda5 to give more room to your installation.

Probably grub will still show win XP, if that bothers you, you can update grub from inside your current ubuntu installation, not from the live CD. update with the command
```

sudo update-grub

```

---

