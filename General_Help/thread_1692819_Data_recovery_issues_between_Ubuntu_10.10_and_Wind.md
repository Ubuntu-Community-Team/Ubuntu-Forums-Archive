---
title: "Data recovery issues between Ubuntu 10.10 and Windows"
date: 2011-02-22
forum: General Help
---

### Post by twin_57103 on 2011-02-22
Hi,

Quick summary: I'm trying to recover 20 Gb of data from an external hard drive that mounts under Ubuntu but not Windows.  I need the data in Windows.

The long version:
After my boyfriend's hard drive crashed, I downloaded Ubuntu 10.10 (x86) to use as a rescue OS.  We have since replaced the hard drive and restored the system to Windows 7 (64 bit).

While running Ubuntu, we mounted his external hard drive to check his backup, which was current.  Since then, we haven't been able to get it to mount on any Windows machine (getting errors that say the drive needs to be formatted), including after mounting and unmounting under Ubuntu (I ran it off a CD disk on my old P3 since my desktop doesn't appear to like 10.10).

I mounted two of my flash drives under Ubuntu, and they have now developed glitches, too.  One didn't mount under either computer (might be the flash drive itself) and the other now tries to open Windows explorer for every drive on my system whenever I insert it.

In summary: I'm trying to get about 20 Gb of data back off a drive that will only mount under Ubuntu.  USB isn't a good option (USB 1.1) and there is no optical burner.  I don't want to risk confusing any more of my external drives (flash or hard drives) by intermixing the two systems.  I have ISO's for some older versions of Ubuntu, which I'm tempted to try since I don't remember having issues like this before.

Any suggestions?

Thanks in advance for any advice!

---

### Post by twin_57103 on 2011-02-22
Anyone?

---

### Post by Jouke74 on 2011-02-22
I suggest you leave Ubuntu, especially on the P3, out of the equation for now since it seems to be destroying your NTFS file systems. Big questions are if you have removed the drives safely and unmounted them properly. 

For the backup recovery I would suggest the two windows tools called GetDataBack and Recuva. Start with Recuva and if that fails to read your disk then try Getdataback. Just plug the drive in the Windows computer. Do not format the drive(!) but start the program and start scanning the disks.

PS. If the data on this disk is crucial, professional help may be more appropriate.

---

### Post by smurphy_it on 2011-02-22
What file system is on the external drive ?  If windows is asking to format it, the drive may think it isn't a format it can recognize.

do a 'sudo fdisk -l /dev/sdX' in a terminal window, and post the results here.  Performing a 'dmesg | grep disk' can let you know which drive it could be.  

NOTE:  If it is the 2nd drive, it would probably be sdb, so put that in the sudo command above.

Clear as mud ?

---

### Post by twin_57103 on 2011-02-23
Well, I found a workaround, ablbeit an obscure and not very satisfying one.  Although 10.10 won't work on my desktop, I have some old version laying around from my dual-booting days, and 8.04 runs fine.  I have 2 DVD burners, and sure enough, I can access the data under Ubuntu and burn a disk that is readable from Windows.  I'll have the added benefit of an additional backup once all is said and done.  

Since this seems to work, I'm not going to monkey around with un-confusing the drive any further, at least until the data is safely off.  I have to go to bed to get to work in the morning, so I'll have to continue this later.

I'll update if any other hiccups arise - hopefully I have a functional solution.  I'd still like to know what went wrong though, since I used to dual-boot and never had any problems with removable (or internal) media like what I've had just now.

Thanks for the help!

---

### Post by twin_57103 on 2011-02-24
OK, another update...I was able to borrow a 40 Gb hard drive from a friend...one that would be OK if it got messed up.  I used Ubuntu 8.04 to copy data from the messed-up drive to the spare, then used that to carry it to other Windows systems.  I could have probably copied directly from 8.04 to my internal drives, but I'm a little gun-shy after this mess.

The friend who loaned me the hard drive said he had trouble with his whole dual-boot system crashing after installing Ubuntu 10 - apparently there are interoperability issues with Windows that weren't there in older versions.  I'm marking the thread as solved although I'm still very frustrated at how it all turned out.

Thanks again for the help!

---

