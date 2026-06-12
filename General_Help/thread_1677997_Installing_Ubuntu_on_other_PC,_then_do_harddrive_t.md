---
title: "Installing Ubuntu on other PC, then do harddrive transplant?"
date: 2011-01-29
forum: General Help
---

### Post by MrRichard on 2011-01-29
Would it be possible if I install Ubuntu on another PC and install Ubuntu with WINE, then rip out the hard drive and insert it into another PC? I'm doing this because I have no PCI slot on my other PC for my network adapter...

---

### Post by ajgreeny on 2011-01-29
Sorry, but I don't understand what the pci slot and wine have to do with this.  It is not essential to have an internet connection to install ubuntu, though it does help, I agree, and with no connection you won't be able to install wine.

If you simply want to know if you can install on one machine and then put the disk in another, the answer is a guarded "yes", though there may be problems with grub and its detection of device names, though it is unlikely if it is the only disk in both machines.

There could also be slight problems of graphic card drivers, but again that should be easy enough to sort out later if necessary.

Final comment:  You really will not get full value from your system with no internet connection and may find it difficult to do what you want.

---

### Post by MrRichard on 2011-01-31
Sorry for being unclear in the first post. I needed to install WINE for Microsoft Office to run, and I had no way of connecting to the internet with the PC requiring WINE and Microsoft Office. 

It was too late for me to install Ubuntu on the machine in question, but now I know what to do with the other PC that will be coming in for a format some time next week. Thanks for the reassurance though :D

---

### Post by snowpine on 2011-01-31
You may find [AptOnCD]("http://aptoncd.sourceforge.net/") useful for installing WINE on the computer with no internet connection.

---

### Post by perspectoff on 2011-01-31
I got a USB wireless adapter at the corner store for about $30. I got a USB ethernet (wired) adapter for $10. Does your PC not have USB ports, either?

Having said that, I have transplanted hard drives as you described several times. The disadvantage of doing that is small, but not zero. During (K)Ubuntu installation, your hardware is analyzed and the OS customized for your hardware. When you move to a new computer, the new hardware may not match the settings that were configured during the original OS installation. Generally the only place this causes a problem are the graphics settings, but it is not a zero-instance occurrence.

Still, if it works the first time, it is a great way of upgrading your computer.

Another method which I prefer these days, though is to merely copy partitions or filesystems (using dd, partimage, or my favorite FSArchiver) from the old hard drive to the new one. This is especially important when moving from a small capacity hard drive to a large capacity hard drive (in which case FSArchiver is definitely my favorite). The disadvantage is that bootup options are dependent on partition designations. 

If you plan to use Grub2 (run from a LiveCD), though (default for recent versions of (K)Ubuntu), it can scan your new harddrive and install OS's located there fairly automatically, and then can (re-)install itself onto the new hard drive in your newly copied partition.

---

### Post by dnguyen1963 on 2011-01-31
> **MrRichard said:**
> Would it be possible if I install Ubuntu on another PC and install Ubuntu with WINE, then rip out the hard drive and insert it into another PC? I'm doing this because I have no PCI slot on my other PC for my network adapter...

I had done this once for my mother-in-law's computer with reservation, but amazing, Ubuntu (8.04 LTS) was up and running without a hitch.  I have not tried this with later version of Ubuntu.

---

### Post by topher-t-mill on 2011-01-31
As long as the drive is sd,a swapping hard drives should not be too much of a problem, as for wine, why bother, when open office will open the windows files and save them as doc files if you wish. Please don't start me on Wine I will only whine!

---

### Post by C.S.Cameron on 2011-01-31
If you stick your HDD in another computer to do the install, it is best if you disable any other HDD in the computer.
If you can't disable the other HDD's make sure you use manual partitioning and then select the new HDD as the target for the bootloader.

---

