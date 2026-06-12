---
title: "Need help with TestDisk and a lost HFS+ partition"
date: 2010-05-22
forum: General Help
---

### Post by highmighty on 2010-05-22
Hi there,

A friend of mine accidentally deleted his 1000GB HFS+ partition (his entire life: pictures, music, videos, etc) while trying to split his HDD into a 800GB HFS+ and a smaller 200GB FAT32 partition. He "needed" this because he was told that his PS3 couldn't read HFS+ partitions but FAT32 partitions only...

Once the 200GB FAT32 partition was finally created he realized that ALL of his precious data, initially stored on the 1000Gb HFS+ partition, was now gone!!!

He tried to undo his changes many times he told me, he tried re-creating that small FAT32 partition, yada yada yada... without any success.

He then called me and asked for help!

Running Ubuntu and knowing the recovery software called TeskDisk, I told him to stop "playing" with his partitions to prevent further damage to his files and then I offered him some help cause I know someone over here (or elsewhere) can help me recover his data!! :-)

Running a "Deeper Search" with TestDisk on his HDD in Ubuntu gives me a lot of info about some "Deleted" HFS+ partitions but then, I'm afraid as of what's next, what should I choose, should I "Write", should I "Backup", why can't I "List files" on those "Deleted" HFS+ partitions found (there are several?!) while it's possible to "List files" under those FAT32 partitions found.

I do have MANY questions to ask regarding the use of TeskDisk and I'm wondering if someone could help me?!

I could and be willing to post some log files, screenshots, etc.

Thank you all for your time and support,

highmighty

---

### Post by 2hot6ft2 on 2010-05-22
[How to: Recover data with testdisk!]("http://ubuntuforums.org/showthread.php?t=387922")
Photorec is good too and it's covered as well in the how to.
:popcorn:

---

### Post by highmighty on 2010-05-22
Thanks 2hot6ft2, I already went through this HOW-TO and, unfortunately, couldn't find answers to my several questions.

It looks like my questions are more specific to the recovery of HFS+ partitions as oppose to "standard" FAT32 and NTFS partitions...

So I'm desperately searching for THAT knowledgeable geek that is out there somewhere and that could help me!

Thanks anyway :)

highmighty

---

### Post by tgalati4 on 2010-05-22
If testdisk is not able to recreate the partitions, get another TB disk and use photorec to recover the data.

man photorec

---

### Post by srs5694 on 2010-05-22
My advice is to get another terabyte disk drive, do a low-level dd copy of the original to the new drive, and then play with recovery options on one drive or the other. If you damage the disk further, you've then got a backup. Just be *very very careful* when entering the dd parameters, lest you copy from the fresh-from-the-factory new disk and overwrite the one you want to recover!

---

### Post by highmighty on 2010-05-23
How should I properly do the "low-level" copy of this HDD? What would be the syntax? Would an image (e.g. using Acronis True Image) of the HDD be ok?

Thanks again for your time,

highmighty

---

### Post by srs5694 on 2010-05-23
> **highmighty said:**
> How should I properly do the "low-level" copy of this HDD? What would be the syntax? Would an image (e.g. using Acronis True Image) of the HDD be ok?

```

sudo dd if=/dev/sda of=/dev/sdb

```

This copies /dev/sda to /dev/sdb. Change those parameters as necessary for your system. As I wrote before (this bears repeating), be *very careful* with the parameters. If you get the if= and of= options reversed for *your system,* you'll end up trashing your hard disk rather than backing it up.

I've never used Acronis True Image, so I have no idea whether it does an adequate job for this sort of thing. It might, or it might do a copy that relies on filesystem data about what's in use in order to speed things up. If the latter is true, it won't make a complete copy and it will be useless for this purpose.

---

### Post by highmighty on 2010-05-25
Thanks srs5694 and others!

I ordered another 1TB HDD but in the meantime I wanted to show you all a screenshot of what TestDisk is giving me so far...

It looks like TestDisk can see several 1TB HFS partitions but they are all located at different sectors on the HDD, does it look normal to you?

Also, there is a "scary" message saying: "The following partitions can't be recovered:", what would you say regarding that message?

Thanks all for your time and support,

highmighty

---

### Post by highmighty on 2010-05-28
Also, the author of TestDisk replied me and I wanted to show you what he had to say:

> > Running a "Deeper Search" with TestDisk on his HDD in Ubuntu gives me a lot of info about some "Deleted" HFS+ partitions but then, I'm afraid as of what's next, what should I choose, should I "Write", should I "Backup"

**Set the partition you want to keep/undelete to P(rimary), *(bootable) or L(ogical) and on the next screen, choose to Write the new partition table**

> why can't I "List files" on those "Deleted" HFS+ partitions found (there are several?!) while it's possible to "List files" under those FAT32 partitions found.

[B]It's only possible to list files from FAT, NTFS and ext2/ext3/ext4 partition. There is no standard opensource library to access HFS+ filesystem.

 	Christophe[/B]

So does this mean that I will never be able of "seeing" his data on Ubuntu because those files are stored on an HFS+ partition?

How can I tell if the partition/data recovery was successful if, no matter what, I can't see HFS+ files on Ubuntu?

Thanks all,

highmighty

---

