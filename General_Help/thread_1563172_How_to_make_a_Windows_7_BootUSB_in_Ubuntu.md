---
title: "How to make a Windows 7 BootUSB in Ubuntu"
date: 2010-08-28
forum: General Help
---

### Post by xVehemencityx on 2010-08-28
Hi.  I have a program for college that I have to use that isn't compatible with Ubuntu, and for that, I need to put Windows 7 back on my laptop.  The only problem is, it won't install from the CD.  I know the CD isn't corrupt.  My computer just won't let me boot from CDs.  My CD Drive makes this horrible clicking noise and won't do anything.  Is there any way I can copy my CD on to a flash drive?

---

### Post by 3Miro on 2010-08-28
[http://www.intowindows.com/how-to-create-bootable-windows-7-vista-or-xp-usb-flashpen-drive-with-a-single-click-must-try/](http://www.intowindows.com/how-to-create-bootable-windows-7-vista-or-xp-usb-flashpen-drive-with-a-single-click-must-try/)

I guess you can either borrow someone else's computer with windows installed on it, or you can install the non OSE version of VirtualBox, install windows within that and then make the bootable usb.

This program may also work with wine, but its a maybe - maybe not.

---

### Post by C.S.Cameron on 2010-08-28
Open the usb in gparted.
Format in NTFS.
Set the boot flag. 
Copy the contents of the Win7 DVD to it.
(or else extract the Win7 iso to it using Archive Manager).

Now you should be ready to corrupt some computers.

---

### Post by Mark Phelps on 2010-08-29
> **xVehemencityx said:**
> Hi.  I have a program for college that I have to use that isn't compatible with Ubuntu, and for that, I need to put Windows 7 back on my laptop.  The only problem is, it won't install from the CD.

Win7 install media doesn't ship on a CD; it only ships on a DVD.

If you genuinely have a CD, and it came with your machine, it's likely a Restore CD, which means, if you DO boot using it, it will most likely completely wipe your drive and reinstall Win7 as it came from the vendor.

---

### Post by jroa on 2010-08-29
> **Mark Phelps said:**
> Win7 install media doesn't ship on a CD; it only ships on a DVD.

If you genuinely have a CD, and it came with your machine, it's likely a Restore CD, which means, if you DO boot using it, it will most likely completely wipe your drive and reinstall Win7 as it came from the vendor.

If that is the case, then wouldn't it have to have a restore partition?  Maybe that is why it won't boot, it is looking for the partition that got overwritten by Ubuntu.  Just a thought.

You may be able to use [VistaPE]("http://www.vistape.net/") or [Win7PE]("http://www.boot-land.net/forums/index.php?showtopic=7250") to boot.  You have to build these boot disks (MS will not allow people download an actual ISO) unless you know someone who has them already.

What is it that you have to do in Windows anyway?  Maybe there is an alternative.

---

### Post by xVehemencityx on 2010-08-29
Sorry, I meant DVD, not CD.  I should've said disc, not CD.  Is Win7PE a legal download?  My school is VERY strict on what we can and cannot download, and I don't want to get in trouble for downloading something that's illegal.

---

### Post by jroa on 2010-08-29
> **xVehemencityx said:**
> Sorry, I meant DVD, not CD.  I should've said disc, not CD.  Is Win7PE a legal download?  My school is VERY strict on what we can and cannot download, and I don't want to get in trouble for downloading something that's illegal.

You can't download it legally, but you can build it yourself legally using Winbuilder software and a legal copy of Windows.  

With that being said, who would know if you downloaded the iso or built it yourself?  The only problem I could see would be if the downloaded iso does not contain the drivers you need.  If you build it yourself, you can add the drivers and software that you want to put on it.  You can also make it run from RAM so you can take the disk out after it boots.

---

### Post by Mark Phelps on 2010-08-30
OK, so you have the actual install DVD -- which comes with WinPE already loaded.  So, there's no value in trying to build a WinPE boot disk, since you essentially already have one.

If you've tried other CD/DVD media and can't boot from them either, then you need to check your BIOS boot settings -- or your CD/DVD drive is bad, or could also be that the lens is dirty (if you use it a lot) and a simple cleaning will restore it to working order.  There are CD/DVD lens cleaning kits you can buy to do the cleaning.

---

### Post by jroa on 2010-08-30
WinPE is basically a lot like DOS, but with functionality for installing Windows onto a new drive from a disk or from a server.  It is not anything like actually running Windows, unless you run Windows from the command line.

Win7PE, on the other hand, is a complete GUI operating system based on Windows 7 that is bootable from a CD.  It is a GUI based OS as apposed to WinPE which is a CLI.  Win7PE should run most programs that are compatible with Windows7.

In short, WinPE is from MS and designed for OEMs to install software on a new computer.  Yes, you can do some stuff with the command lines, but it will probably not run the software that the original poster wanted to run.  Win7PE, VistaPE, and XPE are actual GUI operating systems that can boot a system into a Windows environment.

---

