---
title: "Partitioner deleted MBR... Live CD &amp; TestDisk?"
date: 2006-06-18
forum: General Help
---

### Post by dejay703 on 2006-06-18
Hi guys,

I was installing Ubuntu onto my sister's computer, and I guess I should have defragmented first.  Well, I didn't, and now the partition has the yellow exclamation sign, and says that it's unformated.

I'm guessing just the MBR got deleted, and using something like TestDisk will work.  However, the problem is that I don't having a booting partition anymore.

Normally, I would just take out the harddrive from the laptop and make it external to another computer.  But this stupid Sony VGN-S270 is a real pain to take out the hd (you have to take apart the entire computer...).  So, I'd rather not do this.  Is it possible to just boot off the Ubuntu Live CD and do it?  I saw someone say this on another thread, but I was a little confused because how could I install the program if I am not using any hard drive space because i'm booting from the cd...

If that doesn't work, I think I may just install xp onto another partition... hopefully that works.  Any advice on how I could go about fixing this?

Thanks in advance.

---

### Post by Ramses de Norre on 2006-06-18
Boot up a live disc and run ```
sudo grub-install /dev/
``` complete "/dev/" with the device node of the hard disk you're booting from.

---

### Post by dejay703 on 2006-06-18
Sorry, I'm still new to Ubuntu.  Does that just mount the drive?  What is this going to do, and what steps will I still need to take?

---

### Post by dejay703 on 2006-06-18
OK, so I'm guessing the grub-install installs the grub boot loader which selects between different OS's.  I don't see how that would help my problem of the partitions not having the MBRs anymore though...

---

