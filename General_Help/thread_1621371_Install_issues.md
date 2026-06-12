---
title: "Install issues"
date: 2010-11-14
forum: General Help
---

### Post by cdubea on 2010-11-14
Hey all,  I'm trying to install Lubuntu on an old HP Pavilion XE3 laptop for use in my workshop.  The LiveCD boots and works just fine.

The problem I'm having is in trying to install Lubuntu on the hard disk.

Clicking on the Ubiquity installer allows me to pick a locale and all that.  I am choosing to use the entire disk to install.

At the "detecting file systems" stage, I get the following error:

"Error informing kernel about modifications to partition /dev/sda1.  Device or resource busy...."

At this point it's useless to proceed.  I've reburned the installation cd three times and that makes no difference.

I've successfully installed PClinuxOS LDXE on this machine, but I would rather have Lubuntu than PCLinuxOS.

Some particulars on this machine

Pentium III, 30 gb hd, 256 mb ram

Thanks in advance.

chris

---

### Post by Rubi1200 on 2010-11-14
When you are on the LiveCD, before trying to install, go to System > Administration > GParted and take a screenshot to post here.

Also, go to Applications > Accessories > Terminal and run the following commands (separately) and post the output here:

```
sudo fdisk -lu
```

Thanks.

---

### Post by cdubea on 2010-11-25
> **Rubi1200 said:**
> When you are on the LiveCD, before trying to install, go to System > Administration > GParted and take a screenshot to post here.

Also, go to Applications > Accessories > Terminal and run the following commands (separately) and post the output here:

```
sudo fdisk -lu
```

Thanks.

Firstly, GParted is not installed.  Attempting to do a sudo apt-get install gparted results in an error "Write error (28: No space left on device)

the sudo fdisk -lu results in:

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e68d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    25189919    12594928+  83  Linux
/dev/sda2        25189920    58605119    16707600    5  Extended
/dev/sda5        25189983    29061584     1935801   82  Linux swap / Solaris
/dev/sda6        29061648    58605119    14771736   83  Linux

Disk /dev/sdb: 1966 MB, 1966800896 bytes
232 heads, 57 sectors/track, 290 cylinders, total 3841408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             128     3838079     1918976    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 2, 3) logical=(0, 2, 15)
Partition 1 has different physical/logical endings:
     phys=(238, 231, 57) logical=(290, 54, 42)

Disk /dev/sdc: 77 MB, 77922304 bytes
4 heads, 32 sectors/track, 1189 cylinders, total 152192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              64      152191       76064    6  FAT16

Thanks for any pointers you can provide.

chris

---

### Post by msktje on 2010-12-02
Hello, i've also tried to install Lubuntu and i got simular problems. My system has 265 MB ram and 1 GB swap. The install crashes around the selection of partitions. 
As far as i can see it tries to write something to the tempory memory and than it fails due to no space left just like yours. I don't understand how this is happening as i have more than 800 mb left in swap. 
I've googled, I found someone who had simular problems who mailed it to the developper but he suggested to expand the swap. But after that the tread was not continued. But for me that is not the solution as i have plenty of space left in swap. I will try installing using the alternate installer cd.

---

### Post by msktje on 2010-12-03
I was able to install Lubuntu 10.10 via the alternate install cd found at the site: [http://lubuntublog.blogspot.com/p/downloads.html](http://lubuntublog.blogspot.com/p/downloads.html)

---

