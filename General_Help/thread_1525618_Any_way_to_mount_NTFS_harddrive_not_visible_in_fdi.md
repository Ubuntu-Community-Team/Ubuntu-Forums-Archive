---
title: "Any way to mount NTFS harddrive not visible in fdisk?"
date: 2010-07-07
forum: General Help
---

### Post by greenchance on 2010-07-07
I have a ntfs hard drive (my "C" drive in Windows) and it has some very important data (baby pictures) on it. The drive is, for some reason, very fail-prone. Last time it went out, I used ubuntu to make a windows disk (I have the key, nothing illegal!) and it went to the error fixing part or what have you and fixed it all up. That was a few days ago, and I was working on backing up the picturs but hadn't finished, and it failed again. Now I can't get it to fix the current windows installation, even though it's doing the same thing (making a clicking noise and stalling on boot before eventually giving up and booting to the ubuntu "d" drive.), it will only take me to the part about installing a new copy of windows, which I don't want to do because that would wipe the drive.

So my next idea was to try and get at the pictures through ubuntu, but when I use sudo fdisk -l, it only shows me my ubuntu hard drive.. Is there anything I can do to find and mount the other drive? I really can't afford to take it in to a professional for data recovery, and I've had them charge me an arm and a leg and do nothing but wipe my drive in the past,  so I want to do everything I can to try and get my pictures back myself.

---

### Post by Serpher on 2010-07-07
If the hardrive is making those noises I'm sorry but you're SOL. This happened to me with all my schoolwork on it right before exams and I had OSs and VMs on there for practical exams. If you ever will use data recovery, the more you turn that hardrive on the more data is being permanently destroyed.

---

### Post by greenchance on 2010-07-07
But like I said, we had this problem a few days ago and windows recovery worked and all our files were fine, so it's not a hardware issue, it's a windows being crap issue. (Well, I believe the drive itself has problems because it dies every time we have a power out despite the computer being on a brand new, really expensive surge protector.)

---

### Post by Yarui on 2010-07-07
Just because you have managed to get the drive working again doesn't mean there is nothing wrong with it.  If your drive has been failing you should feel lucky to have gotten it working again.  Be sure you back up all that data because if the drive is acting that unstable I wouldn't trust it to last much longer.

If the drive is, in fact, perfectly fine the first thing I would suspect is that it isn't getting enough power.  Whichever is the case, you will have to replace the troubled part.  If the hard drive is going bad you will have to buy a new one, and if the power supply isn't putting out enough power you will probably need to replace it.

---

### Post by greenchance on 2010-07-07
No, it isn't working again now, it was last time this exact thing happened. Now I'm simply trying to access it long enough to save these pictures.

And could a power out cause the drive to stop getting enough power? (Once the power is back on and the computer is running. Obviously I don't mean while the power is still out.)

---

### Post by greenchance on 2010-07-07
I found [this]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/") which seems promising, but still nothing about if you can;t see the disk to force mount it. :icon_frown:

I'ma force myself to get to sleep, here's hoping someone will be able to help in the morning. ](*,)

---

### Post by Yarui on 2010-07-07
When I say it may not be getting enough power, I mean the power supply could be bad.  That is not an uncommon problem, but the hard drive isn't likely to be the only piece of hardware you are noticing issues with if your power supply isn't functioning properly.  It is much more likely that it is a drive problem.

If the drive won't show up at all there's not much you can do to get the data off of it.  You could try using different cables to see if that works better for you.  Open the case and move a different power cable to the drive and maybe try out a different data cable too.  It's not terribly uncommon for cables of any kind to go bad.  If that doesn't work you could try getting an external hard drive enclosure to see if you have more luck when the drive is in that, but I wouldn't count on it.  If all else fails you can send the drive into a data recovery company.  This is by far the most extreme solution though, and only for extremely important data, since these companies normally charge outrageously high prices to recover data.

---

### Post by TopEnder on 2010-07-07
G,Day greenchange,  I might be on the wrong track but have you looked at/tried  Test DisK (testdisk_6.11-1_i386.deb - this version works on 10.04 Lucid Lynx).

---

### Post by greenchance on 2010-07-07
It doesn't see my "c" drive, either. Just the ubuntu drive. It seemed promising, too. *sigh*

---

### Post by greenchance on 2010-07-07
If I went ahead and reinstalled windows on it, is there any chance I'd be able to use something like photorec to get the pictures back? Or is that way too much of a crap shoot?

---

### Post by JoelOl75 on 2010-07-07
Reinstalling Windows may have overwritten your pictures.  You should have did recovery on it by mounting it read only....  

Even if Windows did reinstall I wouldn't use that drive.

Reinstalling Windows is the worst thing you could've done.  If mounting it was impossible it may be worth trying Spinrite to try to recover the partition.  [http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

Good luck, hopefully your pics are still recoverable.

---

### Post by greenchance on 2010-07-07
We didn't reinstall windows, please read more carefully. We used the recovery option LAST TIME it went down, and we can't use it again for some stupid reason. My last post simply asked if it would be possible to recover the pictures IF we reinstalled.

Also, I found spinrite last night, and it looked like it might work, but how do you get it onto a hard drive that you can't run? That's the only part I don't get, and I couldn't figure it out from their faq.

---

### Post by JoelOl75 on 2010-07-08
You don't install spinrite, it's an ISO image that you burn to a cd and boot off.   Spinrite won't work on a USB drive, you should remove the drive from the USB enclosure and install it directly on a PATA/SATA connector.  Also Spinrite filesystem and RAID agnostic so it will work on any filesystem be it Linux/PC or even MAC (Must be removed from the mac and installed in a PC for checking).  Also on RAID drives, they should be removed from the RAID array before checking.  Check one drive at a time, then they can be put back into the array when complete.

Good luck with the recovery.

---

### Post by Mark Phelps on 2010-07-09
Best data recovery software I've ever used is GetDataBack.

You can download a free trial from the link below:

[http://www.runtime.org/data-recovery-software.htm]("http://www.runtime.org/data-recovery-software.htm")

You will need to install this on a working MS Windows PC, and you will need to connect the failing drive to that PC, either internally or via USB.

The trial version won't actually recover the files, but it will show you what files it found and the chances of recovering them.

---

