---
title: "Dual boot...???"
date: 2009-11-12
forum: General Help
---

### Post by robertcoulson on 2009-11-12
I have an 80gig hard drive....40 gig (Windows XP ) is on the "C" drive and 40gig on the "D" drive (Blank)...Can I install Ubuntu to the already existing "D" drive already partitioned...???
Thanks Bib Bob

---

### Post by ranch hand on 2009-11-12
Yes.

---

### Post by robertcoulson on 2009-11-12
Thank you very, very much...
Big Bob

---

### Post by DGortze380 on 2009-11-12
Probably not.

You will likely need to delete the partition and create a new one in the correct format (ext3) as well as a partition for swap.

---

### Post by ranch hand on 2009-11-12
I think if you just choos largest unused space it should take care of all that in the installer.

Am I missing something here?

---

### Post by DGortze380 on 2009-11-12
> **ranch hand said:**
> I think if you just choos largest unused space it should take care of all that in the installer.

Am I missing something here?

Yes, the largest unused space won't necessarily be the partition he'd like to use.

Better to do it manually.

---

### Post by robertcoulson on 2009-11-12
Wow..Now I am really confused....Maybe I better just give up and continue with XP.
Thanks Bob

---

### Post by OSX@Linux on 2009-11-12
Ubuntu is a great system with many superiorities to Windows XP. The best one is the amount of help and support on this forum.

The Ubuntu installer will allow you to choose which partitions to install on. Just choose the partition that is not the Windows partition and split it to create a swap partition also. If you have any questions, just ask here on the forum.

---

### Post by robertcoulson on 2009-11-12
Yes, I do believe Ubuntu is far better than XP, but my son uses XP for his autocad program for school and I don't want to wipe it out...If I could just install to the "D" partition, it would make me happy, but so many people say yes it's ok and others say no... You can understand my concern..
Bob

---

### Post by DGortze380 on 2009-11-12
> **robertcoulson said:**
> Yes, I do believe Ubuntu is far better than XP, but my son uses XP for his autocad program for school and I don't want to wipe it out...If I could just install to the "D" partition, it would make me happy, but so many people say yes it's ok and others say no... You can understand my concern..
Bob

You can do it, you should just do it manually to ensure you get the results you want.

First, BACK UP IMPORTANT DATA. If you do everything perfectly, there is still always a chance of data loss.

Next, Drive Letters are a Windows thing. C:\ D:\ are arbitrary and your partitions will not be labeled as such in the Ubuntu installer.

What you'll likely find is the first drive on the system identified as sda (could be hda depending on the type of drive)

Each partition then has a number associated with it.

Your windows is stall is LIKELY (not guaranteed, it's a guess) on sda1.

Your "D" drive would then be sda2.

The paritioner is graphically, and it will show you used space on the partition. You say D is empty, so it should be easy to distinguish.

Delete the partition corresponding to your D drive, and create two new ones. One for swap (2x the amount of RAM you have), and the rest of the free space for / (drive root)

Continue with install.

---

### Post by kurtopia on 2009-11-12
Thanks DGortze!
 
This is something that I am going to be doing and I appreciate the way you laid it out.
 
Cheers,
 
Kurt

---

### Post by robertcoulson on 2009-11-12
Thank you DGortze
I will try to use this information...Thanks again
**Bob**

---

### Post by OSX@Linux on 2009-11-12
If your son wants to use AutoCAD, then take a look into Wine or Crossover. Wine is free and Crossover is commercial. They both allow you to run Windows programs under Linux. 

Take a look at them both. They are both basically Wine, but Crossover is easier and well supported.

---

### Post by OSX@Linux on 2009-11-12
oops

---

### Post by robertcoulson on 2009-11-13
Yes, I found out that WINE will allow me to run Autocad (probably 99%) of the functions...Worth while thinking about...Still a little leery about putting Ubuntu on my "D" drive already partitioned.
Thanks Bob

---

### Post by audiomick on 2009-11-13
No need to be scared of it, it's not that hard;)

First thing is, the installer doesn't do anything destructive without clearly asking you first if that is what you want it to do.
This means, as long as you pay attention to what you are doing, you can start it up and have a look at it and bail out if you are not sure about what you are about to do.

Secondly, there is lot's of info around about how to do this. Try having a look in the Ubuntu documentation
Here's a good place to start:
[https://help.ubuntu.com/9.10/switching/index.html](https://help.ubuntu.com/9.10/switching/index.html)

Thirdly, if you have questions about this topic, try posting to the installations & upgrades section.
[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)
 There's lot's of people hanging around there willing to help.

---

### Post by robertcoulson on 2009-11-13
[]("http://ubuntuforums.org/member.php?u=553389")Thanks audiomik

The link "switching from windows" looks interesting....I will read up on dual booting...Thanks very much for your help and information
Thanks Bob

---

