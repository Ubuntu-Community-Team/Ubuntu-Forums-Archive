---
title: "Please Help!!! Please URGENT!!!!"
date: 2010-09-25
forum: General Help
---

### Post by Manifest on 2010-09-25
Ok i really am panicking! i did a really long homework which lasted hours.
first of all i had ubuntu and windows 7 dual boot 
then on windows i did my really long homework then i saved my work and i was in stupid mode i decided to delete the ubuntu partition then I restarted and it said File not found and grub recovery
 
Please help i dont want to do my hw all over again
BTW sorry 4 bad grammar im panicking and in a rush

---

### Post by io5cml4z on 2010-09-25
Woah slow down! So you were in your windows partition, on windows, and you did your homework and saved it on your windows partition? And then you (on windows) deleted your ubuntu partition which DID NOT contain your homework? And then you restarted and you got an error message when you tried to boot into windows...? If that's all correct I don't know why grub would even load if you deleted your ENTIRE ubuntu section... since I'm pretty sure grub is on the ubuntu section. Please explain more. If that's what happened try booting ubuntu off a live cd, and trying to access your homework on that if it's really that important.

---

### Post by 666f6f on 2010-09-25
Hi there,

Panicking may only confuse you and actually make things worse. You can easily *bring Windows back to life* by following those instructions: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392).

---

### Post by jjakspaw6 on 2010-09-25
Try booting from a Live CD. You should be able to access the ntfs partition and copy your files to a flash drive.

---

### Post by 666f6f on 2010-09-25
> **jjakspaw6 said:**
> Try booting from a Live CD. You should be able to access the ntfs partition and copy your files to a flash drive.

+1 :guitar:

---

### Post by drs305 on 2010-09-25
Since you were probably booting via Grub, the MBR contained instructions pointed to the Grub2 boot files on the Ubuntu partition. When you removed the Ubuntu partition, it didn't change the MBR, which still looks for the non-existent Ubuntu partition.

If the MS link in the previous post doesn't suit you, you should be able to restore your Windows boot via the instructions in this thread:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

You will want the section that restores your Windows bootloader.

---

### Post by SeijiSensei on 2010-09-25
Just a hint....

When I sent my daughter off to college this fall, I bought her an [external USB disk drive]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=414&name=External-Hard-Drives&Order=PRICE") to go with her new computer.  The reason?  So she could keep backup copies of her work on the external drive.  I would strongly suggest you consider this option, or at least, buy yourself a [USB flash drive]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=522name=USB-Flash-Drives") for $10-20 and back things up to that.  Never leave yourself in the position where you only have one copy of something important.  Eventually, someday, something will go wrong, and you'll be in the deep doodoo.

Usually it takes a scary experience like the one you describe to motivate people to backup their files.  Good luck getting everything sorted out and working again!

---

### Post by Manifest on 2010-09-26
> **jjakspaw6 said:**
> Try booting from a Live CD. You should be able to access the ntfs partition and copy your files to a flash drive.
Thank you so so much!!!
Fixed
Happy again :)

---

### Post by takisan on 2010-09-26
I've had this problem before: if you have a DOS or W95-ME bootdisk, boot off of it and type fdisk /mbr. It'd wipe the MBR and re-write it for Windows. For NT based lines, run the recovery console off of the Install disc and type fixmbr. Both methods work for XP from what I've worked with.

Best of luck.

EDIT- When installing Ubuntu and dual-booting Windows, the installer re-writes the MBR to load GRUB off of the Ubunt partiton. By deleting the Ubuntu Partition, the MBR couldn't find GRUB in the partition. I've made that mistake before, and now remenber to boot DOS and run fdisk /mbr every time even if I've just had Windows on that computer.

---

### Post by Chris1274 on 2010-09-26
> **SeijiSensei said:**
> Just a hint....

When I sent my daughter off to college this fall, I bought her an [external USB disk drive]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=414&name=External-Hard-Drives&Order=PRICE") to go with her new computer.  The reason?  So she could keep backup copies of her work on the external drive.  I would strongly suggest you consider this option, or at least, buy yourself a [USB flash drive]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=522name=USB-Flash-Drives") for $10-20 and back things up to that.  Never leave yourself in the position where you only have one copy of something important.  Eventually, someday, something will go wrong, and you'll be in the deep doodoo.

Usually it takes a scary experience like the one you describe to motivate people to backup their files.  Good luck getting everything sorted out and working again!

Using Ubuntu One or Dropbox is another good way to back up your files, while also avoiding the extra step of saving files twice.

---

### Post by drs305 on 2010-09-26
Manifest,

Glad you fixed your problem.

Especially since the thread is marked 'urgent', would you please mark it SOLVED via the "Thead Tools" link near the top right of the first post. It will allow 'helpers' to concentrate on unresolved threads. 

Thanks.

Happy Ubuntu-ing.

Added: As the OP has been offline for the past 4 hours, I am marking the thread solved rather than let it remain "Urgent". If the OP wishes, he/she may remove the SOLVED tag when coming back online by using the same link mentioned in the first part of this post.

---

### Post by jjakspaw6 on 2010-09-26
Glad to help!!!

I think someone said something about backups.... I learned the hard way...
Now everything I work on is saved .. 1  to local drive, 2 NAS  3 USB drive... sucks when updating but Ive got used to it.
Online storage is a good choice for some but I'm not aloud to connect to them from my office.

---

### Post by hrickh on 2010-09-26
When someone posts a topic heading of "Please Help!!! Please URGENT!!!!"

It's completely useless for those of us who may want to help you.

Seriously.

</rant off>

R.
==

---

