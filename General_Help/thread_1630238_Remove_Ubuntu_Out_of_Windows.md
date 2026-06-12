---
title: "Remove Ubuntu Out of Windows"
date: 2010-11-24
forum: General Help
---

### Post by BillBillJr on 2010-11-24
Ok, so I've install Ubuntu inside of Windows XP. Now, however, I want Ubuntu to have a completely seperate partition and just remove XP. How do I go about doing that?

---

### Post by Quackers on 2010-11-24
If you want just Ubuntu to be on the disc you just need to boot from the Ubuntu Live cd and in the partitioning stage just choose the "use entire disc" option.

---

### Post by BillBillJr on 2010-11-24
> **Quackers said:**
> If you want just Ubuntu to be on the disc you just need to boot from the Ubuntu Live cd and in the partitioning stage just choose the "use entire disc" option.

Will that erase all of my files or just edit the partition?

---

### Post by Quackers on 2010-11-24
That will completely over-write everything.
Do you want to keep an operating system on there as well, making a dual boot system?

---

### Post by BillBillJr on 2010-11-24
No, I just want to remove the Windows partition.
I don't want any files removed.

---

### Post by James78 on 2010-11-24
I assume you'd rather convert your Wubi install to a full regular install? See if these work for you (don't worry, you should be able to keep all your files and everything).

[http://infoqueue.wordpress.com/2009/01/04/wubi-installation-to-regular-installation/](http://infoqueue.wordpress.com/2009/01/04/wubi-installation-to-regular-installation/)
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

Edit: Now, after converting from Wubi to a full install, you can just use Gparted to remove the XP partition, and resize the Ubuntu one to the full disk, if you wish.

---

### Post by Quackers on 2010-11-24
Did you install Ubuntu inside Windows or Windows inside Ubuntu? Which system was there first?

---

### Post by James78 on 2010-11-24
> **Quackers said:**
> Did you install Ubuntu inside Windows or Windows inside Ubuntu? Which system was there first?
It's very likely he used Wubi to install Ubuntu inside Windows XP.
> Ok, so I've install Ubuntu inside of Windows XP.

---

### Post by BillBillJr on 2010-11-24
> **Quackers said:**
> Did you install Ubuntu inside Windows or Windows inside Ubuntu? Which system was there first?

Yeah, XP was first and then I installed Ubuntu 8.10 inside of it (take that XP!!).
;)

---

### Post by Quackers on 2010-11-24
I agree, so if he removes Windows he removes Ubuntu automatically. Isn't that right? I don't use wubi - just checking :-)

---

### Post by James78 on 2010-11-24
> **Quackers said:**
> I agree, so if he removes Windows he removes Ubuntu automatically. Isn't that right? I don't use wubi - just checking :-)
That'd be correct. So before he removes Ubuntu or XP, he should just use the links I gave earlier, to move the Wubi install to an actual partition, then afterward, he can remove/change/resize Windows XP and the Ubuntu partition to will. :D

---

### Post by Quackers on 2010-11-24
Ah, thanks for the explanation :-)

---

### Post by BillBillJr on 2010-11-24
I'm having trouble repartitioning my drive. I already have GParted installed and LVPM, but when I right-click the partition I want to split I can't resize, it's blanked out.

---

### Post by wilee-nilee on 2010-11-24
Not to convolute anything more here but here is the thread by a local I would say best person at wubi and a regular user who checks in.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

This is for grub2 so you may need to upgrade to grub2 to do this but I'm not sure about doing that in a wubi. Intrepid was grub-legacy.
sudo grub-install -v  
identifies grub installation

---

### Post by Quackers on 2010-11-24
Oh yes, a very knowledgable fellow in all things wubi :-)

---

### Post by wilee-nilee on 2010-11-24
> **Quackers said:**
> Oh yes, a very knowledgable fellow in all things wubi :-)

Oh yes.

Thread starter to be honest your trying to move a OS that is already past the end of life cyle. I would back up what you want and do a fresh install of a OS that is still being updated.
[http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html](http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html)

---

### Post by BillBillJr on 2010-11-24
It'll take forever to download Ubuntu 10.10...
I'll start the download now and finish in the morning,
just in time for Thanksgiving! :)

EDIT: 23 hours and 22 minutes remaining... :P

---

### Post by wilee-nilee on 2010-11-24
> **BillBillJr said:**
> It'll take forever to download Ubuntu 10.10...
I'll start the download now and finish in the morning,
just in time for Thanksgiving! :)

EDIT: 23 hours and 22 minutes remaining... :P

Is it your connection it should download pretty fast.

---

### Post by BillBillJr on 2010-11-24
Yeah probably is. My sister is probably on also, that sucks up a lot of speed too. I usually get 29 - 40 KBPS, but I'm only getting 6.

---

### Post by Quackers on 2010-11-24
Ugh, that's a drag :-( It's like the pre-broadband era again!

---

### Post by James78 on 2010-11-24
> **Quackers said:**
> Ugh, that's a drag :-( It's like the pre-broadband era again!
Gah. Brings back too many memories now. :/ I love my 2mbps connection. Takes me maybe around 15 minutes or so for 1GB. :p

---

### Post by BillBillJr on 2010-11-24
Yeah, we have Verizon and I'm connected through wifi.
Hey, it jumped to 38 KB/S!

---

### Post by Quackers on 2010-11-24
Did your sister fall asleep :-)

---

