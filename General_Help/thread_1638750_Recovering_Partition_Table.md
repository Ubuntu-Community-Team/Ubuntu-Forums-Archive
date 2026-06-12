---
title: "Recovering Partition Table"
date: 2010-12-06
forum: General Help
---

### Post by davidx773 on 2010-12-06
I accidentally overwrote my MBR with an outdated backup of it. I know I had three primary partitions NTFS, ext4 and a swap (in that order). I'm looking to get a couple of files off of the ext4. I tried testdisk, but it doesn't seem to find the ext4, only a fragment of a previous ext3 partition that was on the disk before (and I guess never got fully overwritten yet).

I have an older backup of the files from the system. Is there some log (I looked in dmesg) that may have a copy of the start/end sectors of the partition (which is mounted as "/")? Does anyone have any other methods to maybe find this partition?

Thanks,
David

---

### Post by sikander3786 on 2010-12-06
Welcome to the forums :-)

Just re-installing Grub from an Ubuntu Live CD/USB might work successfully here.

We need to see the output of this boot script for that.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Please wrap your output using proper code tags # from post menu. [/code] at the end and [code] at the beginning.

---

### Post by davidx773 on 2010-12-06
I actually need the partition table from the MBR restored. Unfortunately it's not as simple as just re-installing GRUB (although that's what I was initially trying to do). I'm looking for any ideas on how to recover that by maybe searching through the disk or finding out where the partition was from some log.

---

### Post by shrimpboi13 on 2010-12-08
I think I have a very similar problem. Partition managers on a live CD and  during install don't recognise any partitions however the live cd managed to mount the partitions with all of the data in tact... 

Interestingly an XP setup disc also found my NTFS partition. I suppose that doesn't help access an ext 4 partition though.

---

### Post by Rizwanm on 2010-12-08
Hi i am also having similar problem guys ..... But i think it will help me i will try this :)any ways thanks guys

---

### Post by srs5694 on 2010-12-08
I'm not an expert on testdisk, but I believe it does an initial scan and then gives you an option for a more in-depth scan. Perhaps the latter will find your partition.

Failing that, I'd recommend recovering what partitions you know are correct and then try again with testdisk. If that fails, you may be able to recover your partitions by trial and error with fdisk, and a fair hunk of luck.

---

