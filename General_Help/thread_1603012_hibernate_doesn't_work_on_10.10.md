---
title: "hibernate doesn't work on 10.10"
date: 2010-10-22
forum: General Help
---

### Post by rajanm1 on 2010-10-22
hiya, when i try and hibernate it says the space is not large enough however i have 4GB of space free and ONLY 1GB of RAM (it's a netbook).
how can i get it to hibernate?

many thanks!

---

### Post by imol on 2010-10-22
How big is your swap partition?

---

### Post by rajanm1 on 2010-10-23
> **imol said:**
> How big is your swap partition?

probably not big enough :( how can i make it bigger?

thanks

---

### Post by rajanm1 on 2010-10-24
> **rajanm1 said:**
> probably not big enough :( how can i make it bigger?

Thanks

bump :(

---

### Post by -kg- on 2010-10-24
First, read the information at the link in my signature block.  If you have 1 GB of RAM, you will need at least 1 GB of space in your swap partition in order to hibernate your computer.  Unlike Windows, Linux uses a partition separate from the others for it's "swap" or "paging" files.

If you have less than 1 GB of space in your swap partition, you will need to expand the swap partition, which may involve shrinking one of your other partitions in order to give yourself room unless you happen to have free space right next to your swap partition (which isn't likely).  That's why I refer you to the link in my signature block.  You will need to know what you're looking at.

First, find out how much space you have in your swap file presently.  Open a terminal window and enter the following:

```
sudo fdisk -l
```
(That's a lower case "L", not the number one...you can copy and paste the above, if you prefer)

You're looking for the line that says, "Linux swap / Solaris" behind it. I have just a little over 3 GB swap partition, and my block size with the fdisk command reads "4208998", so I would assume that you need around 1/3 of that block size to approximately equal 1 GB.  If you are much less than that, you will need to expand your swap partition.

Then, if you have any questions, post back.

---

### Post by rajanm1 on 2010-10-24
thanks, it came up with this:

Disk /dev/sda: 7682 MB, 7682605056 bytes
255 heads, 63 sectors/track, 934 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005cbc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         888     7127040   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             888         934      372737    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5             888         934      372736   82  Linux swap / Solaris

Disk /dev/mmcblk0: 16.0 GB, 16039018496 bytes
255 heads, 63 sectors/track, 1949 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000c87a

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1        1863    14957568   83  Linux
/dev/mmcblk0p2            1863        1950      702465    5  Extended
/dev/mmcblk0p5            1863        1950      702464   82  Linux swap / Solaris

it has reformatted the layout here but it is only 372736 for the swap, which im guessing means it isnt large enough. Have you got a how to guide for ubuntu beginners on how to fix this or could you please tell me what i should do/type? (i would be eternally grateful :))

thanks

---

### Post by rajanm1 on 2010-10-26
> **rajanm1 said:**
> thanks, it came up with this:

Disk /dev/sda: 7682 mb, 7682605056 bytes
255 heads, 63 sectors/track, 934 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
sector size (logical/physical): 512 bytes / 512 bytes
i/o size (minimum/optimal): 512 bytes / 512 bytes
disk identifier: 0x0005cbc4

   device boot      start         end      blocks   id  system
/dev/sda1   *           1         888     7127040   83  linux
partition 1 does not end on cylinder boundary.
/dev/sda2             888         934      372737    5  extended
partition 2 does not end on cylinder boundary.
/dev/sda5             888         934      372736   82  linux swap / solaris

disk /dev/mmcblk0: 16.0 gb, 16039018496 bytes
255 heads, 63 sectors/track, 1949 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
sector size (logical/physical): 512 bytes / 512 bytes
i/o size (minimum/optimal): 512 bytes / 512 bytes
disk identifier: 0x0000c87a

        device boot      start         end      blocks   id  system
/dev/mmcblk0p1   *           1        1863    14957568   83  linux
/dev/mmcblk0p2            1863        1950      702465    5  extended
/dev/mmcblk0p5            1863        1950      702464   82  linux swap / solaris

it has reformatted the layout here but it is only 372736 for the swap, which im guessing means it isnt large enough. Have you got a how to guide for ubuntu beginners on how to fix this or could you please tell me what i should do/type? (i would be eternally grateful :))

thanks

bumpy :)

---

