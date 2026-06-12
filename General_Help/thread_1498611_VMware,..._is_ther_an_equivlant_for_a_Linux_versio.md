---
title: "VMware,... is ther an equivlant for a Linux version?"
date: 2010-06-01
forum: General Help
---

### Post by Zerocool Djx on 2010-06-01
VMware seemed to to wonders running Ubuntu in Windows,.. is there anyway to do the other way around now?

---

### Post by Ozymandias_117 on 2010-06-01
Sure, just download and install :P

Although, you may want to try out [Virtualbox]("http://www.virtualbox.org/"). For me it runs faster and has a cleaner interface.

---

### Post by Zerocool Djx on 2010-06-01
Well thank you,... if this works out I will most certainly dump windows completely, lol...

How much faster is the difference? I never had lag before in windows and I can only assume that running in Linux VMware would be better.

Is there a noticeable difference?

---

### Post by xfearxnxloathing on 2010-06-01
VirtualBox

---

### Post by Ozymandias_117 on 2010-06-01
> **Zerocool Djx said:**
> Well thank you,... if this works out I will most certainly dump windows completely, lol...

How much faster is the difference? I never had lag before in windows and I can only assume that running in Linux VMware would be better.

Is there a noticeable difference?

I'm referring to VMware vs Virtualbox. I haven't done any testing or probing to be able to give you definitive answers, I just know from personal experience Virtualbox FEELS faster, plus it is completely free (well, as in beer, only partially free as in speech)

Not to mention all stuff you have to tell VMWare before they will let you download their product turns me off :P

---

### Post by Zerocool Djx on 2010-06-01
OK,.. here is my plans,...

Ultimatly I want to remove windows from it's own partition and just run it in VB/VMware and make Ubuntu the main system.

How do I remove grub and reset the MBR to just load Ubuntu?

How to I clear out the windows partition?

How do I expand Ubuntu's partition?


Anything I am missing?



as far as VMware/VB,... I never used virtual Box, but I use VMware in windows a lot... operating it still the same?

---

### Post by xfearxnxloathing on 2010-06-01
> **Zerocool Djx said:**
> OK,.. here is my plans,...

Ultimatly I want to remove windows from it's own partition and just run it in VB/VMware and make Ubuntu the main system.

How do I remove grub and reset the MBR to just load Ubuntu?

How to I clear out the windows partition?

How do I expand Ubuntu's partition?


Anything I am missing?



as far as VMware/VB,... I never used virtual Box, but I use VMware in windows a lot... operating it still the same?
Applications>Ubuntu Software Center (its at the very bottom), search gparted.

---

### Post by Zerocool Djx on 2010-06-01
> **xfearxnxloathing said:**
> Applications>Ubuntu Software Center (its at the very bottom), search gparted.


Ok,.. I'm assuming that will fix the partition issue... that about grub and the MBR? I just want ubuntu to start on power up and not load grub...

---

### Post by xfearxnxloathing on 2010-06-01
> **Zerocool Djx said:**
> Ok,.. I'm assuming that will fix the partition issue... that about grub and the MBR?

im not exactly sure what you meant about deleting the grub and the mbr, sry.  you can delete, format, move and resize partitions tho.

windows was on the drive first then you dual booted ubuntu?  you should just be able to delete or format that partition and the grub for your ubuntu installation should still work and boot.  you can then move the partition if needed but not necessary.  i would change the filesystem from windows' ntfs or fat 32 to ext3 or ext4 depending on what your ubuntu filesystem already is. im not the greatest at this but im trying to help.

---

### Post by Zerocool Djx on 2010-06-01
> **xfearxnxloathing said:**
> im not exactly sure what you meant about deleting the grub and the mbr, sry.  you can delete, format, move and resize partitions tho.

windows was on the drive first then you dual booted ubuntu?  you should just be able to delete or format that partition and the grub for your ubuntu installation should still work and boot.  you can then move the partition if needed but not necessary.  i would change the filesystem from windows' ntfs or fat 32 to ext3 or ext4 depending on what your ubuntu filesystem already is. im not the greatest at this but im trying to help.


basically what I am asking is on a disk drive Win comes before ubuntu right now on a dual boot,.. if remove grub it will go to windows correct? if I delete the windows partition will it load ubuntu? and if so then I just need to move the ubunto to the front of the disk drive and expand the partition to the whole disk,.. anyone following me?

---

### Post by xfearxnxloathing on 2010-06-01
> **Zerocool Djx said:**
> basically what I am asking is on a disk drive Win comes before ubuntu right now on a dual boot,.. if remove grub it will go to windows correct? if I delete the windows partition will it load ubuntu? and if so then I just need to move the ubunto to the front of the disk drive and expand the partition to the whole disk,.. anyone following me?

if you delete the grub yes windows will only boot from that point on.  if you delete the windows partition only ubuntu will boot and yes i believe you are correct about the expanding.

---

### Post by Elfy on 2010-06-01
This grub and partitioning is in another thread as well ... 

[http://ubuntuforums.org/showthread.php?t=1498643](http://ubuntuforums.org/showthread.php?t=1498643)

Where do you want to deal with it there or here?

---

### Post by Ozymandias_117 on 2010-06-01
DO NOT USE GPARTED!!!

Ok, just wanted to get your attention :P. Make sure you boot to a live CD before you do any partitioning, you never want to work with a partition you're using (Which I assume you will want to put the Windows space into Ubuntu :P). It will be in System -> Admin -> GParted Already installed and ready.

> basically what I am asking is on a disk drive Win comes before ubuntu right now on a dual boot,.. if remove grub it will go to windows correct? if I delete the windows partition will it load ubuntu? and if so then I just need to move the ubunto to the front of the disk drive and expand the partition to the whole disk,.. anyone following me?

No, if you remove GRUB nothing will boot, unless you reinstall the Windows MBR.

If you delete the Windows partition, yes, Ubuntu will still boot fine.

Yup, just move and expand.

Once you boot up after deleting Windows, run ```
sudo update-grub
``` to get Windows off of GRUB.

---

