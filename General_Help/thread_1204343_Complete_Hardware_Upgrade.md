---
title: "Complete Hardware Upgrade"
date: 2009-07-04
forum: General Help
---

### Post by Kunin on 2009-07-04
So tomorrow I'm going to upgrade my very old machine, but I want to keep everything as it is (just replace hardware and move data over).  But I'm not sure what is the best way to do it.

Current system has a mix of 4 IDE drives set up like this:

\ = OS Drive
\home = 2nd drive
\home\<account>\Movies = 3rd
\home\<account>\Movies\backups = 4th drive

Only reason it's like that is I kept running out of space and had limit funds.

New system will use a VelociRaptor (or SSD if I can find a good price) for the OS drive and 2x SpinPoint F1 (RAID 0) for \home (and everything under it).

What is the best way to transfer my current set up over?

I'm thinking the best/easiest way would be to set up the new hardware, and then put in the \ drive (MB I'm getting has support for 2 PATA drives) and then boot up a live CD.  dd over the \ drive, shut down and repeat with \home drive (change the mount so it works).  After that take out DVD drive, plug in both other IDE drives, boot up and copy their data over as well.

Is that the best way, or is there a better way to do it?  If it is... could someone help me with the dd command, I understand, conceptually, how to use it but never messed with it before so don't want to screw things up.

On a slightly related note, what is the best filesystem for the OS drive?  I've heard RFS is because it's faster at handling smaller files.

Thanks.

---

### Post by markharding557 on 2009-07-04
i presume you are replacing the mb,this will require sata hard drives which have different connectors than ide so you will not be able to put your ide drives in it.
most of your old components will not be compatable.
so you will need new:
1 memory(to suit mb)
2 video card(unless using built in one in mb)
3 mb
4 sata hard drive
5 new processor to suit mb.
6 shiny new tower to put it all in
you may be able to reuse old dvd/cd drive
you may want to consider card readers etc
then when all is done you can connect your new m/c to the old one to obtain your data

---

### Post by Kunin on 2009-07-04
Thanks for the reply... but you didn't actually answer my question.  I already know I need new hardware, hence the title of the post is "Complete Hardware Upgrade" and I said I wish to "replace hardware and move data over".  Also stated is the MB I am getting tomorrow has support for two PATA devices, which means it can access the data on the old IDE drives to move to the new SATA drives.

---

### Post by Sef on 2009-07-04
> On a slightly related note, what is the best filesystem for the OS drive? I've heard RFS is because it's faster at handling smaller files.I would stick with ext3, the default file system.   Wikipedia on the [Reiser File System]("http://en.wikipedia.org/wiki/ReiserFS").

---

### Post by 3Miro on 2009-07-04
I will just take out the HD from the old machine, install whatever OS you with on the new one and then connect the old disk to the new machine and move the data. (assuming you know how to do it)

You can hook both machines to a network and use either samba or preferably NFS to move thing over. It will be slower, but you will not have to tinker inside the computer box. (you also need cables + hub/switch/router + setting up samba/nfs)

A solution requiring no (or almost no) knowledge, but largest amount of time, is to use a large USB flash drive and move things that way. It will really take a long time (depending on the amount of information that you have and the size of your USB drive).

If all else fails, you can try burning CDs and/or DVDs and moving the data that way, but this is last resort (only if all else fails for some reason). The only advantage of this method is that at the end you will have a backup copy of everything (which in itself is a good idea).

---

### Post by niteshifter on 2009-07-04
Hi,

Regarding old PATA drives and new SATA drives: For around $20 purchase a USB IDE drive adapter [like this]("http://www.amazon.com/Sabrent-USB-DSC5-3-5-Inch-Converter-Adapter/dp/B000HJ99DI/ref=sr_1_1?ie=UTF8&s=electronics&qid=1246756183&sr=8-1") (amazon.com) (I have this unit - works great). Connect it to the old drive, plug the USB connector in and you're good to go - you've essentially turned your old drive into a USB external HD.

It's also just a plain handy gizzie to have around for when (not if!) systems go down.

---

### Post by Kunin on 2009-07-04
> **Sef said:**
> I would stick with ext3, the default file system.   Wikipedia on the [Reiser File System]("http://en.wikipedia.org/wiki/ReiserFS").

Thanks, what about these various threads I've read about using noatime and alignment if I get the SSD?

---

### Post by Kunin on 2009-07-04
> **3Miro said:**
> I will just take out the HD from the old machine, install whatever OS you with on the new one and then connect the old disk to the new machine and move the data. (assuming you know how to do it)

You can hook both machines to a network and use either samba or preferably NFS to move thing over. It will be slower, but you will not have to tinker inside the computer box. (you also need cables + hub/switch/router + setting up samba/nfs)

A solution requiring no (or almost no) knowledge, but largest amount of time, is to use a large USB flash drive and move things that way. It will really take a long time (depending on the amount of information that you have and the size of your USB drive).

If all else fails, you can try burning CDs and/or DVDs and moving the data that way, but this is last resort (only if all else fails for some reason). The only advantage of this method is that at the end you will have a backup copy of everything (which in itself is a good idea).


I'm no stranger to the inside of a computer, so that was what I was planning on doing.  Network is also an option, but would be very slow compared to just sticking them both in the same box (temporarily).  

Issue I have is I have a lot of customized scripts/oddball packages installed/etc that I've added over the years and honestly don't remember what they all are... at this point it's more of "Yeah, I did something to make this work" so I don't want to do a fresh install and reinvent the wheel.  My assumption is that (after setting up the RAID array and formatting the drives) I should be able to boot off the live cd, mount new OS drive as write, and copy the old OS drive over (then repeat for the other stuff).  Anyone see a reason why that wouldn't work?

---

### Post by 3Miro on 2009-07-04
> **Kunin said:**
> I'm no stranger to the inside of a computer, so that was what I was planning on doing.  Network is also an option, but would be very slow compared to just sticking them both in the same box (temporarily).  

Issue I have is I have a lot of customized scripts/oddball packages installed/etc that I've added over the years and honestly don't remember what they all are... at this point it's more of "Yeah, I did something to make this work" so I don't want to do a fresh install and reinvent the wheel.  My assumption is that (after setting up the RAID array and formatting the drives) I should be able to boot off the live cd, mount new OS drive as write, and copy the old OS drive over (then repeat for the other stuff).  Anyone see a reason why that wouldn't work?

Other than issues with hardware drivers, it should work. However, I have never done it and I have never seen/heard anyone doing it.

---

### Post by blueridgedog on 2009-07-04
> **Kunin said:**
> 
\ = OS Drive
\home = 2nd drive
\home\<account>\Movies = 3rd
\home\<account>\Movies\backups = 4th drive
...  dd over the \ drive, shut down and repeat with \home drive (change the mount so it works).  After that take out DVD drive

Well, I hope you new rig has an SATA DVD...

Personally I would not use dd as that would bring over everything as fragmented as it is.  If you use rsync, you can clean things up a bit.

Personally, I would get the new system up and running, debugging all hardware issues then mount your older drives and rsync the data over.

---

### Post by Neural oD on 2009-07-06
Have you had a look at remastersys - google it!

---

