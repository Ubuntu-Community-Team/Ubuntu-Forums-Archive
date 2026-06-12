---
title: "Partition editor trouble?"
date: 2010-02-23
forum: General Help
---

### Post by KajiKindorai on 2010-02-23
Hi I seem to have a unique issue and after browsing the threads for some time I have found no other topics similar to my own... I have a Dell AMD TTurion dual core 64 bit laptop that I am trying to recover with ubuntu. No other operating systems have been able to boot or repair anything from my previous vista installation. The trouble is, wether I start from live disk, or directly try to boot from the installer on the disk, the partition editor does not detect any partition whatsoever, nor will it let me create a new one, its as if my C:/ drive doesn't exist at all. I cannot for the life of me figure out how to fix this... Please assist! Im pulling my hair out here...

---

### Post by bodhi.zazen on 2010-02-24
If you are having problems across multiple OS it is sounding like a hardware problem.

Can you put the drive in another system ?

---

### Post by KajiKindorai on 2010-02-24
lol its in a laptop, im not particularly wonderful at disassembling them. The only other computers I have are 32 bit desktops... Not to mention this drive is run on sata and my desktops are all IDE

---

### Post by warp99 on 2010-02-24
Download dban:

[http://www.dban.org/](http://www.dban.org/)

See if it detects the drive. If so "nuke" it, then install ubuntu.

---

### Post by KajiKindorai on 2010-02-24
i cant get my desktop to burn the image to a disc lol

---

### Post by warp99 on 2010-02-24
You can make a USB boot disk using a Windows machine or install to a floppy in Linux. The how to is in the readme.txt file.

---

### Post by Mark Phelps on 2010-02-24
> **KajiKindorai said:**
> lol its in a laptop, im not particularly wonderful at disassembling them. 
Generally, all you need to do to remove a hard drive from a laptop is remove one screw and gently pull out the drive -- at least, from the half a dozed different model laptops I've used.  Look around on the back on your case for such screws.  There's typically two -- one for the system memory, the other for the hard drive.

> The only other computers I have are 32 bit desktops... Not to mention this drive is run on sata and my desktops are all IDE
Computer stores typically sell an adapter kit that allows you to connect a PATA or SATA drive and then plug the cable into a USB port on your desktop.

---

