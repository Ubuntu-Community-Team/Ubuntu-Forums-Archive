---
title: "Partitioning drives -- Round to cylinders"
date: 2010-07-10
forum: General Help
---

### Post by shaggy999 on 2010-07-10
I have some questions regarding the "round to cylinders" (referred to as RTC for the rest of this post) option in parting drives. My understanding is that this used to be done to maximize efficiency on the disk, but that modern hard drives no longer have a 1:1 correspondence with the way RTC was designed to work -- meaning a cylinder isn't exactly one cylinder on a modern hard drive anymore. This is even less important with SSD drives as there are no cylinders and access times are equal across the entire drive.

"Though CHS values no longer have a direct physical relationship to the data stored on disks..."
Source: Wikipedia: [http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

The reason I'm asking is because I'm writing a script that sets up a hard drive and installs a custom Ubuntu installation. In my script I have the following lines:

NOTE: $BLOCK_DEVICE = /dev/sda in this case.
```

parted -ms "$BLOCK_DEVICE" -- mkpart primary 63s 257039s
parted -ms "$BLOCK_DEVICE" -- mkpart primary 257040s -1s

```

parted defaults to taking a number and specifying the number of MBs to take up, which is fine except that fdisk then complains that the partitions don't fall on cylinder boundries. So I obtained the numbers by first creating partitions the way I want in gparted with RTC enabled and then right-clicking each partition and clicking on "information" which tells me what sectors a partition occupies. The "-1s" in the second line means "fill the rest of the drive with this partition".

The really weird thing is that if I create the partitions with gparted fdisk doesn't complain, but if I used parted to create the partitions with the exact sector values that gparted calculated I *sometimes* get fdisk errors regarding cylinder boundries and *sometimes* I don't. Very weird.

So I basically have two questions:

1) Should I even care about sector boundries when creating my partitions? I tried using the "--align" option in parted, but it didn't seem to do anything. In my particular case it's an SSD, but does it matter anymore with a modern hard drive too?

2) If it does matter, how might I calculate sector values on my own to match cylinder boundries? It looks like there's approximately 8 MB per cylinder so if I convert partition size to MB, divide by 8, then multiply by (255 tracks x 63 sectors = 16065) I should get a sector count for the approximate space I want for the partition that can fit to cylinder boundries. I think I have to subtract 1 from that.

---

