---
title: "Paranoid about MBR - please confirm"
date: 2010-05-07
forum: General Help
---

### Post by yxlbaz on 2010-05-07
I have a redundant XP system on /dev/sda1 (first partition first disk).

GParted flags this as "boot"

I would like to reformat this ntfs partition as ext3 and use it as another ubuntu system for testing stuff.

My main question is whether a reformat can affect the MBR on this boot disk.  I think it can't but I would really welcome confirmation from someone who has done it and survived.

Thanks

---

### Post by srs5694 on 2010-05-07
"Master Boot Record (MBR)" can refer to at least two things:


[list]
[*]The first sector of a hard disk, generically. This usually holds both first-stage boot loader code and a partition table to define four primary partitions.
[*]The partitioning system that defines four primary partitions in the first sector of the hard disk, with logical partitions defined elsewhere.
[/list]


I suspect you're meaning "MBR" to refer to the boot loader in the MBR (first definition), or perhaps to the MBR (first definition) itself. The literal answer to your question depends on your intended meaning, and also how you "reformat" the partition.

If you create a new filesystem by using the text-mode mkfs or mke2fs program, that program will affect the contents of the partition you specify, but will not affect the MBR, in any meaning of the term. Therefore, the answer to your question would be "no, it won't;" however, to do a complete job, you should then manually adjust the partition type code of the partition using fdisk or a similar utility, and this will necessarily modify the partition table -- but not the boot loader.

If you create a new filesystem by using GParted, then the partition table will be slightly modified because the partition type code will change. This should not affect the boot loader code.

Ultimately, I think you're asking if you'll damage your system's bootability. The answer is "probably not," but there are some peculiar boot configurations that could be damaged by creating a new filesystem on /dev/sda1. Overall, I'd say you should probably go ahead and do it, but you should first prepare yourself by downloading a copy of [Super GRUB Disk](http://www.supergrubdisk.org) and ensure that your Ubuntu install CD/DVD is in good order. You could use one of these to recover from problems, should one occur.

---

### Post by lmarmisa on 2010-05-07
Hi yxlbaz,

In my humble opinion, you can format your NTFS /dev/sda1 partition if you use the grub (or grub2) program as loader.

You can see the structure of the MBR in thins link:

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

If you format the /dev/sda1 partition, the first 446 bytes  of the MBR (the code area where the object code of the loader is stored) will remain untouched.

You will need to make some adjusts in the grub/grub2 config files, editing and deleting the XP entry in the **/boot/grub/menu.lst** in the case of grub or typing the command **sudo update-grub2 **in the case of grub2.

Best regards,

Luis

---

### Post by yxlbaz on 2010-05-08
OK - Thanks for that. Confidence seriously restored and some new stuff learned.

---

