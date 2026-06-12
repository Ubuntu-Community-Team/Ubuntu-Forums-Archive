---
title: "install on a logical drive?"
date: 2011-10-01
forum: General Help
---

### Post by Oxyris on 2011-10-01
I have a new laptop and since windows 7 is really confusing I'm installing ubuntu (I had a mac before which i was in the process of dual booting with linux until it got stolen). 
This new laptop is a refurb and it originally had a recovery partition but everything was wiped and instead there are now 3 partitions: 

a random primary partition (i'm guessing this is the boot partition but it doesn't say that. the C: drive says system, boot, page file, active, crash dump, primary partition) that is about 12 gb; 

another primary partition, the C: drive containing the os, 116 gb; 

and a logical drive called data, designated as drive D:, 337 gb.

I had no idea what a logical drive and, after researching a bit, to be honest I'm still a bit confused. I've googled the problem obviously but I'm just not sure what to do. 

should i format the logical drive (it's NTFS) and put ubuntu there or can i just install it without doing any prior work? should i just shrink the windows partition (about 30 gb of that 116 is used) and plant ubuntu in the free space there?

any advice would be greatly appreciated. Thanks

---

### Post by coffeecat on 2011-10-01
Very quickly, as I need to be logging off soon, you are limited to four primary partitions with an mbr-type partition table - which is what you have. Windows must be on a primary partition. Or at least its boot files must be. A data D:/E:/whatever drive may be a logical partition. That's partition not drive. A drive is a physical piece of equipment. A partition is part of a drive defined by code written to the drive. Except when Windows calls a partition a drive. Clear? :wink:

To get around the 4 limitation, you can have one only extended partition which is just a special type of primary partition, but whose sole purple is to act as a container for logical partitions. I don't know what the limit is for the number of logical partitions, but it's more than you or I will need.

The good news is that Linux can boot from a logical partition. It doesn't have the limitation that Windows has in this respect.

Your D: so-called drive will be in an extended partition. If you look closely in Windows' Disk Management tool, you will probably see this graphically. You could shrink the D: "drive", and then create more Linux logical partitions in the freed space, and keep the D: "drive" which will be seen and be usable from Ubuntu.

Have a look here for more. Read all the links:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

And good luck!

---

