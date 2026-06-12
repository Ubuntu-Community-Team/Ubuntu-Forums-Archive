---
title: "Adding more gigs to a different partition"
date: 2010-07-22
forum: General Help
---

### Post by leviathan8 on 2010-07-22
[B]Hello. I am using ubuntu 10.04 and I would like to move some gigabytes on another partition.
On dev/sda/9 I have 90 GB. I would like to move them to another dev/sda that is located on windows.
My linux partion is ext3 format, and the other ones are ntfs. I would like to move around 50 GB to an NTFS partition from an ext3. 
I have some questions regarding to this.

1. What program do I use?
2. What I have to do before moving gigabytes.
3. What I have to do after making changes.
4. What are the risks?

I experienced a bad grub fail last month - so I couldn't boot anything after making a new partition - so I am a bit scared of playing around with this.
Thanks.
[/B]

---

### Post by leviathan8 on 2010-07-22
**Bumping           .**

---

### Post by Rubi1200 on 2010-07-22
Hi,

first things first, you need to post the output of this:

```
sudo fdisk -l
``` (lowercase L not 1)

Second, it is considered a breach of netiquette to bump your post after such a short time (the minimum is 24 hours).

Please remember that all the people here on the forums are visitors, users, and volunteers. If someone has time, great. If not, please be patient until someone comes along with an answer.

:)

---

### Post by leviathan8 on 2010-07-23
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02a602a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       38245   204798976    7  HPFS/NTFS
/dev/sda3           38245       63741   204798976    7  HPFS/NTFS
/dev/sda4           63742      121602   464760832+   f  W95 Ext'd (LBA)
/dev/sda5           63742       76490   102400000    7  HPFS/NTFS
/dev/sda6           76490       80314    30720000    7  HPFS/NTFS
/dev/sda7           80314       89238    71677952    7  HPFS/NTFS
/dev/sda8           89238      108853   157559808    7  HPFS/NTFS
/dev/sda9          108854      121602   102398976   83  Linux

```

**This is my fdisk, and sorry for bumping so fast, but the thread went to 2nd page and had no visits.**

---

### Post by leviathan8 on 2010-07-23
[B]Poster below, I already figured it out. Thanks :p
[/B]

---

### Post by Mark Phelps on 2010-07-23
You bumped in only two hours! What about NOT bumping within 24 hours are you incapable of understanding??

Basically, you can't MOVE space from one partition to another.  All you can do is shrink one partition and enlarge another.  And if the two partitions aren't adjacent, you have to move the intermediate ones around (left or right) to "move" the unallocated space until it's adjacent to the partition you want to enlarge.

---

