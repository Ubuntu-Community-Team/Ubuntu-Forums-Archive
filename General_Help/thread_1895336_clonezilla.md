---
title: "clonezilla"
date: 2011-12-14
forum: General Help
---

### Post by Gwaro on 2011-12-14
I cloned one partition having ubuntu 11.04 to a different partition, but i have a problem restoring the cloned image back. Is it possible to restore such an image to a different partition but on the same drive?

---

### Post by x C0MMAND0 x on 2011-12-14
I believe if you imaged /sdaX you have to restore it to /sdaX , but I'm not completely sure...

---

### Post by collisionystm on 2011-12-14
> **Gwaro said:**
> I cloned one partition having ubuntu 11.04 to a different partition, but i have a problem restoring the cloned image back. Is it possible to restore such an image to a different partition but on the same drive?

Is it just not letting you restore at all? Or is it letting you restore but you just cannot boot from it

---

### Post by haqking on 2011-12-14
you can restore an image to any drive or partition you like as long as the destination is equal or larger in size.

What problem exactly are you getting ? an error message ?

---

### Post by seawolf167 on 2011-12-14
You can restore any partition to any available partition provided the destination partition exists and its size is greater than or equal to the source imaged partition's size.

I haven't had any problems with this. I recently transfered individual partitions from a hdd to a ssd one at a time on a dual boot system with no issues other than having to reinstall GRUB since I did it partition-by-partition.

---

### Post by Gwaro on 2011-12-14
> **collisionystm said:**
> Is it just not letting you restore at all? Or is it letting you restore but you just cannot boot from it


It is not letting me restore it at all

---

### Post by Gwaro on 2011-12-15
> **haqking said:**
> you can restore an image to any drive or partition you like as long as the destination is equal or larger in size.

What problem exactly are you getting ? an error message ?


The error message is : Failed to restore partition image file /home/partimg/ubuntu-11.04-img/sda2* to /dev/sda2! Maybe this image is corrupt or there is no /home/partimg/ubuntu-11.04-img/sda2!

---

### Post by haqking on 2011-12-15
> **Gwaro said:**
> The error message is : Failed to restore partition image file /home/partimg/ubuntu-11.04-img/sda2* to /dev/sda2! Maybe this image is corrupt or there is no /home/partimg/ubuntu-11.04-img/sda2!

did you do a integrity check on the image and is the destination there ?

---

### Post by Gwaro on 2011-12-16
Finally got it going! Thank all of you. Found that i had located a smaller partition that the original one. Everything is  now ok.

---

### Post by haqking on 2011-12-16
> **Gwaro said:**
> Finally got it going! Thank all of you. Found that i had located a smaller partition that the original one. Everything is  now ok.

cool, you are welcome.

Cheers

---

### Post by seawolf167 on 2011-12-16
> **Gwaro said:**
> Finally got it going! Thank all of you. Found that i had located a smaller partition that the original one. Everything is  now ok.

If everything is working properly please mark this thread as Solved under Thread Tools :)

---

