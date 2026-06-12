---
title: "So, Don't Hate Me..."
date: 2009-11-13
forum: General Help
---

### Post by Draclvr on 2009-11-13
...but I really tried the Ubuntu 9.10 release.  Loved it initially when my wireless worked, but overnight it decided to take a vacation.  After trying every suggestion out there trying to get my wireless internet to work, I finally gave up. Here's the deal...

Built this computer last spring with this setup:
3 500 GB hard drives; 1 has Windows Media Center on it, 1 has the Windows 7 RC and 1 is unused so far.
1 160 GB hard drive with XP Home on it

I thought I would toy with the new Ubuntu release.  Installed it in a partition on the Windows Media Center hard drive as it was going to be toasted anyway after I did the official Windows 7 upgrade. After 12+ hours of trying to get my wireless to work on the Ubuntu partition, I gave up. It was using the GRUB loader to bring up all my drives and the Ubuntu partition for booting. Fine - pretty cool actually until it started adding over a minute to my boot time. I double checked my boot.ini file on the Media Center partition to make sure it hadn't been altered to the GRUB loader and thought I would be good to delete the Ubuntu partition. HA! Big mistake again on my part. Called myself a bad name and had a beer.

It turns out that the GRUB loader from Ubuntu had installed itself on my Windows 7 Release Candidate hard drive. What? How did that happen?  Nope, can't boot that drive. Had another beer.

Is there any way to get rid of the GRUB loader on this drive which I cannot boot up?  Booting from the Windows 7 DVD is not helping.  Assistance needed before this 62 year old grandma turns into a lush....

---

### Post by fluffman86 on 2009-11-13
First of all, I could have solved your long boot problem: your computer was starting out by booting a hard drive that did *NOT* have grub on it.  Rearranging the boot order would have fixed that.

Now, to get windows to boot again now that grub is gone, you'll need to fix your master boot record.  By default, grub overwrites that with essentially a small file that points to the rest of grub.  And if you delete your ubuntu partion (with grub), then that little file has no where to point.

In Windows XP, this was solved by booting from the XP CD, choosing the Recovery Console, and typing "fixmbr"

Hopefully that will lead you to the right information on how to do that with Win7, or maybe your XP drive.

---

### Post by sledge73 on 2009-11-13
We won't hate ya. Most of us might just have a beer with ya! :D

---

### Post by Draclvr on 2009-11-13
Thanks, guys.  I've changed the boot order so many times, I think I will be dreaming about it.  The problem is that when setting the "problem" drive to boot, it will not recognize the F8 option to use the repair option with the Windows 7 DVD in the drive bay.  So I have to try do the repair from the drive which does not have the GRUB loader on it.    

I've used the fixmbr command numerous times to no avail.  I've booted from the Windows 7 DVD and done the repair thing in the command screen numerous times.  I have no doubt that I'm doing something wrong, but I think I'm at the point where I will retrieve all the files and info I can from the Release Candidate drive and reformat.  I was a dummy to have assumed the GRUB loader would install on the same drive I partitioned to install Ubuntu 9.10.  Lesson learned.

Yup, got a headache and yup, gonna have another beer.

Thanks again!

---

### Post by fluffman86 on 2009-11-13
Do you still have an XP cd?  Set your boot order to boot directly from CD, and unplug all of your hard drives except for XP.  Then run fixmbr on that.

---

### Post by Draclvr on 2009-11-13
But, the XP drive doesn't have any issues.  The drive that Ubuntu installed the GRUB bootloader on is my Windows 7 Release Candidate drive.  Which I can no longer access because I gave up on getting my wireless to work and deleted the partition on the old Media Center drive.  I can boot into my old XP Home drive and my "formerly Media Center, now Windows 7 upgrade" drive just fine.

I'd reinstall Ubuntu on one of my drives just so I could do the repair before I deleted the partition, but I'm afraid of where it might install the GRUB loader this time.  

I REALLY wanted to make this OS part of my system, but I've just spent WAY too many hours trying to make it work.  Think I'll go kill a bunch of zombies in Left 4 Dead to work off a little frustration.....

---

### Post by jimmy the saint on 2009-11-13
I could be mistaken, but I think he was using the XP example to illustrate that runnning the windows installation disk usually gives you the option to restore the bootloader.  I can't say for certain because I don't have much experience with Windows anymore, but I would imagine Win7 has a similar feature to repair the installation (and bootloader).

[http://lmgtfy.com/?q=windows+7+repair+bootloader](http://lmgtfy.com/?q=windows+7+repair+bootloader)

---

### Post by PRC09 on 2009-11-13
Found the post below for the win 7 boot repair.I would unplug your other drives tho before using this guide and just leave the win 7 drive connected.This should resolve your problem...

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Draclvr on 2009-11-13
Thanks for all your replies.  I've used the boot repair to no avail also.  However, the one thing I haven't done is unplug all the other drives.  That will be my next attempt.

---

### Post by Mark Phelps on 2009-11-13
> **PRC09 said:**
> Found the post below for the win 7 boot repair.I would unplug your other drives tho before using this guide and just leave the win 7 drive connected.This should resolve your problem...

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

+1 -- excellent reference!  Used it myself recently to restore boot to a Win7 multi-boot machine.  

Had to do the command line bootrec stuff.  For reasons yet to be explained, the menu selection of Startup Repair doesn't seem to be able to actually do the repairs!

As to unplugging your drive -- you need to first find out which drive has the following in the root directory for the MS Windows install: bootmgr (file), boot (folder).  Those are the bootloader files for Win7.  My guess, if you had XP installed already when you installed Win7, is that those files are in the XP partition -- because Win7, when installed to a box that already has XP (or Vista) installed, will reuse the OS partition of the previous OS to store its boot loader files.

This can make recovery very complex when the XP partition is on a different drive than the Win7 installation.

---

### Post by Draclvr on 2009-11-13
Deer season starts tomorrow, so won't have a chance to get back into this until next week.  As I was nervous about the Windows 7 RC installation last May, I unplugged the XP drive when I installed Windows 7.  I'd checked on this before and this drive does have the files you mentioned.  I just can't get to them because of the GRUB loader.  I'm thinking of just unplugging all the drives, but that one, reinstalling Ubuntu 9.10 on it so I can at least boot up.  Maybe I can repair it from there.  I'd love to keep the Ubuntu on a partition, but it refuses to work with my wireless.  I just built this computer in March and don't particularly want to start replacing what are basically brand new components.

---

### Post by Draclvr on 2009-11-15
Got a nice deer yesterday and I'm back at this.  Success is reported with the Startup Repair utility finally!   I am now able to boot into any of my 3 operating systems.

I'd like to NOT give up on Ubuntu and am going to post elsewhere on recommendations for an Ubuntu distro that might work on my old 98SE computer.  It only gets to about 20% of the installation for 9.10 and stops.  I think I'd like to try an older one...

Thank you much for all your help on keeping me out of the rehab clinic!

---

