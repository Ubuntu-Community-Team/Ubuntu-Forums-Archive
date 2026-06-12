---
title: "Extending hard disk size after hard drive regrow from 8 to 20 GB preserving data  da"
date: 2010-12-23
forum: General Help
---

### Post by albertwt on 2010-12-23
Hi All,

I wonder if this is possible to extend or regrow the Linux hard disk partition from 8 GB to 20 GB without losing the existing data on the partition ?

at the moment this Ubuntu Linux is deployed on top of VMware and I've just regrow the hard drive from 8 GB into 20 GB but can't see the effect immediately.

can anyone suggest how to do this without losing the data ?

and I found some strange error message when i do the fdisk -l ?


Thanks,

Albert

---

### Post by Quackers on 2010-12-23
Have a look at post #2 in the link below. Is that what you want?

[http://ubuntuforums.org/showthread.php?t=1242394&highlight=resize2fs](http://ubuntuforums.org/showthread.php?t=1242394&highlight=resize2fs)

---

### Post by albertwt on 2010-12-23
> **Quackers said:**
> Have a look at post #2 in the link below. Is that what you want?

[http://ubuntuforums.org/showthread.php?t=1242394&highlight=resize2fs](http://ubuntuforums.org/showthread.php?t=1242394&highlight=resize2fs)

wow, thanks for the help,

so [PHP]resize2fs -p /dev/sda1[/PHP] is the command that i need to execute ? does it scale all of my partition proportionally ?

or can I do this on the server through SSH console ? since this is production server.

Thanks.

---

### Post by psusi on 2010-12-23
You didn't say what you did to try and grow the partition.  You should have used gparted.  If you just used fdisk to delete and recreate the partition with a higher end point, then you need to run resize2fs, which will expand the filesystem in the partition to use the full size of the partition.

---

### Post by albertwt on 2010-12-23
> **psusi said:**
> You didn't say what you did to try and grow the partition.  You should have used gparted.  If you just used fdisk to delete and recreate the partition with a higher end point, then you need to run resize2fs, which will expand the filesystem in the partition to use the full size of the partition.

ah ok, so in conclusion:

use FDISK + resize2fs to resize but the data will be lost
use GParted to resize without dataloss ? --> can I do this in command line ? because my server system doesn't have GUI.

---

### Post by albertwt on 2010-12-23
well, I guess resize2FS doesn't work if I don't use the FDisk command before to reformat the whole / partition.

---

### Post by psusi on 2010-12-23
If you do it right, you will not loose any data with fdisk.  gparted is the easiest and safest method, but if this is a remote server you only have command line access to, then you might need to do the fdisk method.  The trick to doing it right is to put it into sector mode with the -u switch, and make sure that you recreate the partition with exactly the same starting sector, and an ending sector further down the disk ( that does not overlap another partition ).

---

### Post by albertwt on 2010-12-23
> **psusi said:**
> If you do it right, you will not loose any data with fdisk.  gparted is the easiest and safest method, but if this is a remote server you only have command line access to, then you might need to do the fdisk method.  The trick to doing it right is to put it into sector mode with the -u switch, and make sure that you recreate the partition with exactly the same starting sector, and an ending sector further down the disk ( that does not overlap another partition ).

wow, so the data will still be available right ?
"**put it into sector mode with the -u switch, and make sure that you recreate the partition with exactly the same starting sector, and an ending sector further down the disk ( that does not overlap another partition **."

might have to try to get the list of all available sector then.

---

### Post by psusi on 2010-12-24
Yes, changing the partition table does not actually modify the data on the disk ( other than the partition table itself ), so as long as you recreate the partition exactly as it was before ( or longer ), no data is lost.

---

### Post by hello2012 on 2010-12-27
[FONT=Times New Roman][SIZE=3]Or you can through Partition Assistant to finish your target operations.[/SIZE][/FONT]

---

