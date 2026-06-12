---
title: "Really need help restoring MBR"
date: 2009-09-19
forum: General Help
---

### Post by linkxs on 2009-09-19
Hi there,

I had win 7 + ubuntu 9.04 and I accidentally erased mbr, forgetting that it'd kind of kill the partition table. how would i restore it? I really need to have it back up by midnight (5 hours).

There are about 8 or 9 partitions there.

Please help me, i need to finally start working!

Thanks for any help.

---

### Post by ankspo71 on 2009-09-19
Hi,
I restored my grub by using this tutorial
[http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/](http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/)
It worked great for me in Ubuntu 9.04
Hope this helps
James

PS. this will help the bootloader installed by ubuntu, not win 7

---

### Post by linkxs on 2009-09-19
i tried it and got stuck on the part after 

root (hd0,

Let me remind you that the partition table is empty, just shows empty space.

---

### Post by ankspo71 on 2009-09-19
Oh, then the partition table is probably gone then like you said. I'm afraid I don't know what to do in that case. I'm sure someone will come along soon and help you out.
James.

---

### Post by Tipped OuT on 2009-09-19
> **linkxs said:**
> Hi there,

I had win 7 + ubuntu 9.04 and I accidentally erased mbr, forgetting that it'd kind of kill the partition table. how would i restore it? I really need to have it back up by midnight (5 hours).

There are about 8 or 9 partitions there.

Please help me, i need to finally start working!

Thanks for any help.

Pop in a Windows XP/Vista/7 installation disk. Go into recovery mode and enter this command, "**fixmbr**". Done.

---

### Post by linkxs on 2009-09-19
just tried fixmbr from win 7 inst. cd, that did nothing.

---

### Post by htroyo on 2009-09-19
i have a similar problem, i tried to restore the grub via live cd and i have problems, but if you are able to access the partitions try copying your files into win 7 partition and use the windows installation disk to destroy linux partitions maybe it will write a new partition table (i haven't tried it because i have not where to put my files...)

---

### Post by linkxs on 2009-09-19
I can't access the partitions at all! they are empty space. If i could access them, I would back up and reinstall everything

---

### Post by confused57 on 2009-09-19
I've never used TestDisk, but it may be what you need:

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by Tipped OuT on 2009-09-19
> **linkxs said:**
> I can't access the partitions at all! they are empty space. If i could access them, I would back up and reinstall everything

Maybe because there are no partitions with an operating system installed? They're empty, which is why "fixmbr" did not work for you.

Only hope is to sacrifice a partition to temporarily install an operating system on, and back up the files from the other partitions from there.

---

### Post by linkxs on 2009-09-19
i was thinking of waiting until tomorrow to get my sata external enclosure and use testdisk on a windows machine. do you think that will work?

---

