---
title: "Opinios Please"
date: 2010-10-24
forum: General Help
---

### Post by alphaamanitin on 2010-10-24
Hey Guys,

So yesterday I accidentally used GParted to delete, and reformat my windows HD on my dual boot machine from from NTFS with the OS installed, to FAT32.  I would like to recover the data.  Does anyone have opinions on software to use?  I am willing to pay for the software as well.  

Alternatively, are there any Ubuntu utilities to use to recover the data?  I immediately turned off the machine, which was running Ubuntu at the time.  I plan to unplug the drive before turning it back on and booting into Ubuntu, good idea?  Or is it okay to leave it plugged in?  My understanding is that most of my data should still be there, is this right?  

I couldn't think of a better place to pose my solicitations for opinions.  

Thanks,

AlphaA

---

### Post by wojox on 2010-10-24
You could try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

---

### Post by JC Cheloven on 2010-10-24
Hi, from [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

> If you made a mistake while partitioning and the partition no longer appears in the partition table, so long as you have not written data in that space, all your data is still there. 

So, your worries should be only moderate ;)

In that link you'll find several recovery tools, along with some wise advice about procedure. Wojox's advice (testdisk) among them.

Offtopic: please note for future cases how helpful the ubuntu community documentation may be!

---

### Post by alphaamanitin on 2010-10-24
Thanks for the links.  I have read quite a bit about this, but I was really hoping for opinions on procedures and software that have been used.  So if any one has ever done this I would like to hear about the success rate of it.  Also, I can't find this stated in simplicity, but use dd to clone the HD to a new drive and working from there should not cause any data loss correct, and will prevent me from damaging my chances of getting data back?  I was going to use dd if=/dev/sdY of=/dev/sdX  where Y is the original drive that got formatted, and X is a new drive of equal size (250 GB)?  From there I was going to try the testdisk stuff, find the back up NTFS info, try to restore and restore the NTFS boot sector.  Thoughts?  I am sorry, I know this is not a windows forum, but the steps would pretty much be the same for Ubuntu as well right?  Also, this is the only forum I find helpful.

Thanks,

AlphaA

---

### Post by alphaamanitin on 2010-10-26
Hello All,

I was able to use TestDisk to completely recover the NTFS parition.  I used Super GRUB to rebuild the Window's XP MBR and now everything works exactly like it did before the 'accident'.  Just thought I would let everyone know.

AlphaA

---

### Post by katykat on 2010-10-27
Thank you. 

I had been looking for a Linux solution to fix the Win MBR. 

Another i believe is ms-sys. 

Please advise if there are any peculiarities about Supergrub....

---

### Post by alphaamanitin on 2010-10-27
> **katykat said:**
> Thank you. 

I had been looking for a Linux solution to fix the Win MBR. 

Another i believe is ms-sys. 

Please advise if there are any peculiarities about Supergrub....

yeah it is not exactly intuitive.  Before you do anything make sure you know the drive locations.  hdX or sdX  when I was rebuilding my XP MBR I used hd0.  My copy at least acts very oddly to me.  If I select WIN + WIN MBR I just boot into windows.  I have to first do the choose langauge, then I choose english, then I select windows and from there on I cannot remember exactly what to do without looking at it, sorry.  If I have time tonight I will look back into it and tell you the steps I take to rebuild the MBR.  Alternatively, if you can get your hands on a installation disk of whatever windows you are using it is much easier to repair and Microsoft actually has goo instructions on that-but you wanted a linux solution.  

I will try to get back with the supergrub steps.  I found them on a website once, but oddly enough it was not on SuperGrub's website and I cannot remember where I found it.  I know, not much help:(

sorry

AlphaA

---

