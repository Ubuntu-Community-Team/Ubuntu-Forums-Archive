---
title: "no module name found"
date: 2010-08-24
forum: General Help
---

### Post by sean.bailey00 on 2010-08-24
I've fought with this issue for a couple of weeks and cannot seem to crack it, so I thought I'd ask if anyone has any useful suggestions.  I couldn't find anything in my search of the forums, but if I missed it, please give me the link.

So...

I recently purchased a Dell Studio 14, with Windows 7 64-bit.  It has the i5 processor, and 6GB of Ram, so I went with the 64-bit version of 10.04.  I've never used the 64-bit version, but I've had Ubuntu since 6.10, so I&#7743; pretty familiar with it.

The install goes fine, and the OS works perfectly.  When I restart, everything is great, GRUB works fine, etc.  The problem occours when I boot into Windows.

After restarting from Windows, the laptop powers up, then, where it would usually boot GRUB, I get this error:

> no module name found
Aborted. Press any key to exit.

Then, after pressing any key:

> Broadcom UNDI PXE-2.1 v 12.2.0
Copyright (C) 2000-2009 Broadcom Corporation
Copyright (C) 1997-2000 Intel Corporation
All rights reserved.
PXE-E61: Media test failure, check cable
PXE-M0F:Exiting Broadcom PXE ROM.
Operating System not found.

At that point, pressing any key starts the error sequence over again.  At first I thought GRUB may have corrupted, so I reinstalled it from the Live CD.  After a few hours of finagling, I reinstalled Ubuntu, which resolved the problem.  I thought.  Until I booted into Windows again.  Now, I'm back where I started.

I go back to college tomorrow, so I'd like to have my computer working... and I'd hate to have to wipe out the Ubuntu partitions.  Any ideas would be welcome.

Thanks!

---

### Post by sean.bailey00 on 2010-08-24
Also, out of curiosity, I installed 10.04 32-bit, since I'm not familiar with glitches in the 64-bit version, and got the same error, which leads me to believe that Windows 7 is screwing up the MBR somehow... any ideas?

---

### Post by bleutyler on 2010-08-24
I have gotten this error too, just today.

I have a Dell Inspiron 17 laptop.  I did my research and it has good reviews on this forum.

It came with windows 7.  I installed Ubuntu 9.10 on a seperate partition and I had dual boot enabled.  That installed fine.  Updated to 10.04, also fine.  Today was the second time I booted into windows.  That went fine.  I did a clean restart, and now I get this error immediately when I boot up.  No Grub, nothing.  

I have determined that this is a 64 bit machine, so I am currently getting the v10.04 64-bit ISO file and I will try it on the Inspiron.  

I really have no idea why this error all of a sudden came up.  I _knew_ that my incredibly smooth Ubuntu installation was too good to be true!!   :frown:

---

### Post by sean.bailey00 on 2010-08-24
So 9.10 worked fine?  I kind of liked it better anyway.  I wonder if downgrading will fix it.  Guess I'll give it a try...

I tried asking Dell support (since they have machines with Ubuntu on them) but, not surprisingly, dual booting is not allowed, and they wouldn't even talk to me.

---

### Post by sean.bailey00 on 2010-08-24
OK, looks like [this solution]("http://ubuntuforums.org/showthread.php?t=1343851&page=2") worked for some people, though I have not tried it yet (yeah, I guess there was another thread).

Apparantely some Dell-specific software is screwing with the MBR every time it runs... that's why it effs up every time you boot Windows.  I'm going to try this now... I hope it works.

I really hope that this fixes it.

---

### Post by sean.bailey00 on 2010-08-24
> **sean.bailey00 said:**
> OK, looks like [this solution]("http://ubuntuforums.org/showthread.php?t=1343851&page=2") worked for some people, though I have not tried it yet (yeah, I guess there was another thread).

This is the most comprehensive solution from that thread:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

---

### Post by colin.p on 2010-08-24
Uninstall Datasafe. I have a 1545 that dual-boots 7 and 10.04. I got rid of Datasafe (don't even know what it's supposed to do anyway)a month ago and absolutely no more problems booting into 7 or lucid.

---

### Post by sean.bailey00 on 2010-08-24
So, just like in the other thread, uninstall those Dell Data Safe applications, and you're golden!  Running well.

And those stupid aplications are for amatures anyways.  I had a funny feeling about applications that come pre-loaded too.  I usually delete them all to begin with.

---

### Post by bleutyler on 2010-08-25
Well, I reinstalled GRUB with the 10.04 live CD, and I am posting from the PC; so it got me back into Ubuntu.

I will try that solution you posted sean, but for now I am going to run some backups.  

Sean:

Yes, 9.10 installed without an issue on the Dell Inspiron 17.  But I did not use it at all.  The first thing I did when the installation was complete was upgrade to 10.04.

Are your partitions getting out of hand?  I have 6 which seems a bit high for a dual boot.

---

### Post by colin.p on 2010-08-25
Off hand, I'm not sure of the maximum amount of partitions, but, on my Dell, I have 3 primary partitions(win 7, a Dell utility and a restore partition). I think there is a 4 primary partition limit, however.
I installed ubuntu to an extended partition, then made 2 logical partitions (plus a swap)in the extended, for a grand total of 6 partitions. I decided (for the time being) to keep the setup as is, but everything seems to be getting along, at the moment.

---

### Post by radioactivepeach on 2010-09-12
Hey guys! I had the same problem with my dell studio with w7 64bits. I installed ubuntu 10.04 in a new partition, as some people in the thread have commented. So, the key seems to be to unistall Dell DataSafe. Great, but how do I go to w7 to uninstall the software if the pc does not even recognize any operating system? (same message: "module name not found" etc etc.) I'm not a big computer geek... :(
Thanks! ;)

---

### Post by ancaleth on 2011-01-21
You should have a Windows 7 CD to boot from and then deinstall.

Same problem here on dual boot on 64-bit laptop with Windows 7 and Ubuntu 10.10. Because of random mouse / keyboard freezes, I was checking the filesystems using Windows - to see if the freezes only occured with Ubuntu - and it crashed. Since then, booting is not possible.

The message is:[INDENT]> Realtek PCIe GBE Family Controller Series v2.29 (06/30/09)
PXE-E61: Media test failure, check cable
PXE-M0F: Exciting PXE ROM
Operating System not found
no module name found
Aborted.
Press any key to exit [/INDENT]I had had a problem with grub before and had solved it by rewriting the mdr. It hadt worked well.

I'm kind of worried it is a hardware problem and not just because of a program pre-installed by Dell.


EDIT: I reinstalled grub from the Live CD. sda7 being the Partition on which Ubuntu 10.10 is installed. Presto manifesto, everything is back. (The original problem is still there, I guess, but I'll tackle that later)

```
sudo mount /dev/sda7 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

---

