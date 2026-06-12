---
title: "SiI 3512 eSATA boot problem - an exercise in frustration"
date: 2010-01-12
forum: General Help
---

### Post by melgish on 2010-01-12
I have a Dell Optiplex GX620 that's been giving me grief ever since I decided to add additional storage.

I'm running Ubuntu 9.04 Server (x64) and my goal is to get this [_RAID enclosure_]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817332020") connected using it's eSATA port instead of the USB port that it's using now.

My first attempt was to use an adapter cable and connect to the internal SATA port.  That was before I discovered that Dell decided to save $0.0000001 by not soldering the 2nd SATA connector to the motherboard.

So that failed and I ended up purchasing this [_Rosewill eSATA-150 card._]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816132025")  The card as a Silicon Image SiI 3512 chipset.

Not wishing to risk my RAID data until everything else is working, I'm currently testing with this [_external bay_]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817392022") and a 40G WD SATA drive.

So the problem is that Ubuntu doesn't seem to recognize the drive when I boot up. Only the system drive shows when I 'fdisk -l'  However If I boot with the box powered off, and then switch it on once the system is up... I can then access the drive.  

I've been all over the internet looking for a conclusive solution.  I've tried booting with irqpoll option and that wasn't any help.

I suppose I can yank the card and go back to using the USB interface, but that has [_it's own issues noted here._]("http://ubuntuforums.org/showthread.php?t=1200587")

If anyone has one of these cards working flawlessly, or can help me troubleshoot, I'd sure appreciate the help.

---

