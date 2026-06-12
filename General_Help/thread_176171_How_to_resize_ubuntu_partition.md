---
title: "How to resize ubuntu partition"
date: 2006-05-14
forum: General Help
---

### Post by Hoffmann on 2006-05-14
Hello:

I would like to move my /home folder to its own Ubuntu partition. I already know how to do that.
My only problem is: how to resize my current partitions?
I have no free space on my HD. Its partition scheme is:
(a) Windows xp (NTFS) 
(b) Linux Swap
(c) Ubuntu (ext3)

My goal is to get some free space, create a new partition on it, and move my /home stuff into it. How could I resize those partitions (a)-(c), so? I took a look on GParted program, but I didn't feel very confortable. I see that I would need to umount partitions, etc. and I didn't feel so secure about that. If that program is really the only alternative for my case, could anyone give me some hints? Is there any other alternative?

Thanks,
Hoffmann

---

### Post by steve.horsley on 2006-05-14
You can never unmount you / partition, so you cannot do this from within your normal Ubuntu system. It'd be like doing open heart surgery on yourself.

gparted do a downloadable live CD image. 
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
This is my suggestion.

---

### Post by Hoffmann on 2006-05-14
[QUOTE=steve.horsley]You can never unmount you / partition, so you cannot do this from within your normal Ubuntu system. It'd be like doing open heart surgery on yourself.

gparted do a downloadable live CD image. 
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
This is my suggestion.[/QUOTE]
Thanks for your prompt reply!
Yes. That was the reason I didn't feel confortable with GParted. I would never unmount my / partition. Is it possible to do that with the GParted live CD? I mean, am I going to unmount / with the live CD? How can the resizing be done with the live CD?

---

### Post by tajreed on 2006-05-14
How exactly does one use the downloaded live image to resize a partition. I want to split my HD into a boot partition with Dapper and a data partition.

---

### Post by Hoffmann on 2006-05-14
[QUOTE=tajreed]How exactly does one use the downloaded live image to resize a partition. I want to split my HD into a boot partition with Dapper and a data partition.[/QUOTE]

Well, it seems like nobody knows how to resize linux partition here. Or that is not possible to do safely. Unfortunately, programs such as PartitionMagic seems to work just for Windows. So, probably, that is a good oportunity for improving/changing something on linux in this regard.

---

### Post by jonnyfive on 2006-05-14
I recently had to do this. But I also have a windows xp partition (Dual boot) and a partition adjusting program, partition magic or something.

Anyways, I just adjusted the partition sized from partition magic and bam bigger partition without any problem whatsoever.

---

### Post by Hoffmann on 2006-05-14
[QUOTE=jonnyfive]I recently had to do this. But I also have a windows xp partition (Dual boot) and a partition adjusting program, partition magic or something.

Anyways, I just adjusted the partition sized from partition magic and bam bigger partition without any problem whatsoever.[/QUOTE]


Did you succeed in adjunsting your partitions with PartitionMagic? I realized that since I installed Ubuntu, I cannot use PartitionMagic from my Windows partition anymore. Could you, please, let me know you did that?

---

