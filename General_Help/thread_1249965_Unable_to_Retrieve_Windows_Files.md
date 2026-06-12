---
title: "Unable to Retrieve Windows Files"
date: 2009-08-26
forum: General Help
---

### Post by DerfBWH on 2009-08-26
Hello,
I just installed Ubuntu 9.04 onto a seperate partition last night, when things went rather awry.
The install completed successfully, it said, but when it rebooted the only line that comes up says "No bootable disc found." I am not able to boot into either my Windows partition of my Ubuntu partition.
However, I am able to mount and access my Linux files while booted into the LiveCD - however, I have no such luck with my Windows files.
GParted reports my Windows partition as an "Unknown" file system, and BootIT NG claims that there are errors on the disc and will not boot. I tried the Windows installer's bootup repair tool, and while it says that the Boot Sector is corrupt, it says it can't fix it. I've tried BOOTREC.exe /fixmbr, BOOTREC.exe /boot, SuperGrub, nothing works.

I have a DP35DP with a 3.0 GHz Core 2 Duo and a 1TB HDD split into two partitions - a 800GB Windows, and a 50GB Linux.

Thanks so much, I'd just like to get a file or two back...

---

### Post by SunnyRabbiera on 2009-08-26
Hmm, strange.

---

### Post by DerfBWH on 2009-08-26
Yeah, it just kind of stinks because I had a couple of projects I've been working on all summer and would love to get them back - but I'm not sure if that's in the cards.

---

### Post by DerfBWH on 2009-08-26
Please, please, if somebody can help me, I'd LOVE it.

---

### Post by bchurchill on 2009-08-27
So your master boot record has been corrupted.  Go ahead, boot into the live CD and follow the instructions here:

[https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows)

I'm not sure what you were using before... but these instructions will install GRUB and allow you to dual boot properly.  Initially you might only be able to boot into your new Ubuntu install, but you can modify /boot/grub/menu.lst to add instructions to boot windows.

---

### Post by DerfBWH on 2009-08-27
That didn't work. The system is now unrecognized as a valid NTFS partition. Basically, Ubuntu's corrupted the partition itself some how, which is peculiar because I didn't even use the Ubuntu partition tool to do this. If it was as easy as this, I'd be ecstatic - but I tried that, and failed.

---

### Post by bchurchill on 2009-08-27
> **DerfBWH said:**
> That didn't work. The system is now unrecognized as a valid NTFS partition. Basically, Ubuntu's corrupted the partition itself some how, which is peculiar because I didn't even use the Ubuntu partition tool to do this. If it was as easy as this, I'd be ecstatic - but I tried that, and failed.

You're not giving us much to help you with.  Questions:

0.  What partitioner did you use?  The one in the Ubuntu installer is very easy to use and very reliable (dual booting is a breeze, very simple).  You should try it next time.

1. Did you follow those instructions?  Did GRUB install correctly?  If you can mount your Ubuntu system this is just about fail-proof.  What happens when you turn your computer on?

2.  If GRUB installed correctly where does it not work?  What error messages does GRUB give you?  If windows is not in the list you'll need to add it manually.

3.  In particular, where are you getting this error that your system "is not recognized as a valid NTFS partition"?  Is this from some windows bootloader?  It doesn't know what it's doing.  Use GRUB instead.

 Of course your hard drive isn't an NTFS partition: it has a master boot record, an NTFS partition and at least one EXT3 (or other) partition.  So what you need to do is go into ubuntu and used ```
sudo fdsik -l
``` to see your partitions and figure out what's NTFS and what's EXT3.   If you find the device name for your windows partition (say /dev/sda__) then you can do 

```

sudo mkdir /windows
sudo mount -t ntfs /dev/sda__ /windows

```to mount your windows partition on Ubuntu and see your Windows files.

---

### Post by SuaSwe on 2009-08-27
I think he meant that when attempting to mount Windows using the LiveCD, it returns a 'Not a valid NTFS filesystem' error. That's what it sounded like to me, at least!

I've recently repaired a knackered Windows installation by running the R-for-Repair option using a Windows setup CD. E.g., you press "Enter" to install Windows, then once it lists your partitions, select the relevant one and hit R for Repair.

Unfortunately, this always, always brings with it the risk of data loss, and your case sounds like it may be more severe. :/ Will see what I can find out for you!

Out of curiosity, what partitioner did you use?

---

### Post by SuaSwe on 2009-08-27
If worse comes to worst, there are paths to data recovery that may well help you. See for instance:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

