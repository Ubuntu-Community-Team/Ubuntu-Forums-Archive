---
title: "I am running Ubuntu hoping to fix my Windows... can anyone help me?"
date: 2011-11-16
forum: General Help
---

### Post by Hertz381 on 2011-11-16
I got Ubuntu up and running because I want to fix my windows that is unable to start. 

What is happening is that it is getting stuck on crcdisk.sys when I try to safe mode boot, and just lingers on the loading screen in normal boot. I found this solution... 
> 
My first message was deleted by Dell, presumably for inappropriate language and harassment of their fine company. I will attempt to re-post my response in a more gentlemanly manner.

Ahem...

Now, for your solution: There is nothing wrong with your hard disk, there technically isn't anything wrong with Vista either. The system, believe or not, didn't freeze on crcdisk.sys. It froze after that. What's the first thing that executes, even before logon.sys finishes loading? The answer is ANTI-VIRUS.

Whatever you are running for AV spazzed out because you installed something, and it created some sort of corrupted temp file or protected memory space which in turn caused it to spaz out again and halt your system. If you can get to a command or recovery prompt, you can run a chkdsk /f. I guarantee you that chkdsk will freeze up when it gets to the messed up file. You can either write down the file name and delete it, which might buy you enough time in windows to stop the AV service, but if AV froze up during a hardware or driver install, it will probably recreate the error again. Your best bet is to do it the sloppy way, delete the entire AV directory so that it can't run. Reboot your system, reinstall AV, then uninstall it properly and get a new AV. I recommend Avast!, its free, it ten times better than Norton and Mccrapee, and runs on half as much resources.

If it wouldn't be too much trouble, please inform the aforementioned company that you are no longer interested in their inferior products and services, as you will obtain future products from a more responsible party.

Thank you, this concludes my presentation, best of luck with your endeavors.

-Darryl

 TL;DR - Run "CHKDSK /f" and delete what files are causing your Anti-Virus to lock up.
I could not do this because my disk drive is broken, and my safe mode is not working to go to command prompt. So I installed Ubuntu which has Terminal (same as command prompt right?) but while trying to run CHKDSK /f it says it is an unknown command... what do I need to do to be able to run this? 

 *TL;DR - How can I run CHKDSK /f (windows command) in Ubuntu???*

If not is it possible to do a system restore of windows, from Ubuntu?

Thanks for the help!

---

### Post by jocko on 2011-11-16
> **Hertz381 said:**
> ***TL;DR - How can I run CHKDSK /f (windows command) in Ubuntu???***
You can't. AFAIK there is no linux program that can run a full check on an ntfs file system.
There is a program named "ntfsfix" that claims to find and fix some common errors and set windows to do a chkdsk on the next boot, but that of course requires you to be able to boot windows...
To learn more about that, read the manual (type "man ntfsfix" in a terminal).

> **Hertz381 said:**
> If not is it possible to do a system restore of windows, from Ubuntu?
No. That's not possible.

---

### Post by davetv on 2011-11-17
You could boot using your Windows cd, and go to "Recovery Console" - this is like a dos prompt. From there you should be able to run chkdsk.

---

### Post by HermanAB on 2011-11-17
Howdy,

In general, it is best to use Windows tools to fix Windows.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
[http://www.mytechguide.org/8091/download-windows-7-vista-system-repair-recovery-disc/](http://www.mytechguide.org/8091/download-windows-7-vista-system-repair-recovery-disc/)

---

### Post by Hertz381 on 2011-11-17
> **jocko said:**
> You can't. AFAIK there is no linux program that can run a full check on an ntfs file system.
There is a program named "ntfsfix" that claims to find and fix some common errors and set windows to do a chkdsk on the next boot, but that of course requires you to be able to boot windows...
To learn more about that, read the manual (type "man ntfsfix" in a terminal).


No. That's not possible.

I tried typing man ntfsfix into terminal and it said it did not exist. Thanks anyways. 

> **davetv said:**
> You could boot using your Windows cd, and go to "Recovery Console" - this is like a dos prompt. From there you should be able to run chkdsk.

I can't do this because my disk drive is broken. That is why i'm trying to use Ubuntu.

---

### Post by Hertz381 on 2011-11-17
> **HermanAB said:**
> Howdy,

In general, it is best to use Windows tools to fix Windows.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
[http://www.mytechguide.org/8091/download-windows-7-vista-system-repair-recovery-disc/](http://www.mytechguide.org/8091/download-windows-7-vista-system-repair-recovery-disc/)

I cannot do this because my disk drive is broken...however I am trying to get these files burned to a USB drive that I can boot up, but my Flash Drives are too small at the moment. 

I am trying to do this without paying anything (at the moment at least) because I am really tight on cash... I can't afford to pay 100$ to take it to get fixed, or even 40$ to buy a disk drive.

---

### Post by bcschmerker on 2011-11-17
Is the hard drive operational from a hardware standpoint?  The BIOS setup utility will ID the hard drive(s) in your system.

Toward the end of 2010, my eMachines®/Acer® EL1210-09, running Microsoft® Windows® 6.0.6001 at the time (since rebuilt as a KUbuntu® rig with a new hard drive) would not boot consistently; the problem turned out to be a thermal issue with the controller board on its stock Hitachi® HDP725016GLA380 SATA hard disc, which would not read or write at normal operating temperatures.  (Upon teardown, I suspected a design flaw in the EL1210-09 that prevented cooling air from reaching the controller board; I now have KUbuntu® on a physically smaller Western Digital® WD5000 unit in a custom shock mount.)

Assuming that the HDD has full read/write available (which was not the case with the aforementioned Hitachi® HDD), File System Checker, /sbin/fsck.nt5, should be able to find any major file system problems; but Windows-specific tools are needed for the rest of the repair process (see also my old Thread [Cross-OS System file editing](http://ubuntuforums.org/showthread.php?t=1635591), concerning my search for LinUX tools for fixing major errors in a Windows Registry short of running /opt/wine/bin/regedit.exe in a Wine environment).

---

### Post by Mark Phelps on 2011-11-17
The Boot-Repair utility can repair Windows boot problems as well as Ubuntu -- see the link below:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

In the text, it mentions that you can write it to a USB stick -- and use that to boot.

Also, if you were running Vista, there is no Recovery Console in Vista.  It was eliminated when that came along.

---

### Post by 3rdalbum on 2011-11-17
> Your best bet is to do it the sloppy way, delete the entire AV directory so that it can't run. Reboot your system, reinstall AV, then uninstall it properly and get a new AV.

That's from the thing you posted.

I'd suggest following that - delete every trace of the anti-virus program (if you had one) using Ubuntu. As I understand it, running the 'chkdsk' command was just a way of seeing what file is causing the problem; chkdsk does not fix the problem.

---

### Post by Hertz381 on 2011-11-17
> **3rdalbum said:**
> That's from the thing you posted.

I'd suggest following that - delete every trace of the anti-virus program (if you had one) using Ubuntu. As I understand it, running the 'chkdsk' command was just a way of seeing what file is causing the problem; chkdsk does not fix the problem.

Yeah I tried this and it did not work...so I was hoping to run 'chkdsk' to find the file I need to delete, and then run in safe mode, and restore to a few days back. 


> **Mark Phelps said:**
> The Boot-Repair utility can repair Windows boot problems as well as Ubuntu -- see the link below:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

In the text, it mentions that you can write it to a USB stick -- and use that to boot.

Also, if you were running Vista, there is no Recovery Console in Vista.  It was eliminated when that came along.

Ok I will try this next and Update you guys. 

> **bcschmerker said:**
> Is the hard drive operational from a hardware standpoint?  The BIOS setup utility will ID the hard drive(s) in your system.

Toward the end of 2010, my eMachines®/Acer® EL1210-09, running Microsoft® Windows® 6.0.6001 at the time (since rebuilt as a KUbuntu® rig with a new hard drive) would not boot consistently; the problem turned out to be a thermal issue with the controller board on its stock Hitachi® HDP725016GLA380 SATA hard disc, which would not read or write at normal operating temperatures.  (Upon teardown, I suspected a design flaw in the EL1210-09 that prevented cooling air from reaching the controller board; I now have KUbuntu® on a physically smaller Western Digital® WD5000 unit in a custom shock mount.)

Assuming that the HDD has full read/write available (which was not the case with the aforementioned Hitachi® HDD), File System Checker, /sbin/fsck.nt5, should be able to find any major file system problems; but Windows-specific tools are needed for the rest of the repair process (see also my old Thread [Cross-OS System file editing](http://ubuntuforums.org/showthread.php?t=1635591), concerning my search for LinUX tools for fixing major errors in a Windows Registry short of running /opt/wine/bin/regedit.exe in a Wine environment).

I am pretty sure my HDD is still read / write available because I could access all of its files from Ubuntu, and I saved the ones I needed.

---

### Post by bcschmerker on 2011-11-17
As I understand things, Microsoft® Windows® 6-up has a Startup Repair feature from one of the boot menus having access to Safe Mode.  What success with Startup Repair?  If that, too, runs into a fatal stop (the affected File and cause of crash should be readable when the BSOD appears), a factory reinstall may be necessary.

(Carbonite® kept a ready backup of my documents, excepting Cakewalk® documents kept in C:\Cakewalk Projects rather than an appropriate subdirectory of C:\Users, when I had need for a Win 7 reinstall; more details available at the [Carbonite® public Website](http://www.carbonite.com/).)

---

### Post by Hertz381 on 2011-11-17
> **Mark Phelps said:**
> The Boot-Repair utility can repair Windows boot problems as well as Ubuntu -- see the link below:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

In the text, it mentions that you can write it to a USB stick -- and use that to boot.

Also, if you were running Vista, there is no Recovery Console in Vista.  It was eliminated when that came along.

Ok I did boot repair and it did not work. Here is the link it told me to provide...if this helps any of you thanks! 

[http://paste.ubuntu.com/741896/](http://paste.ubuntu.com/741896/)

---

### Post by Hertz381 on 2011-11-17
> **bcschmerker said:**
> As I understand things, Microsoft® Windows® 6-up has a Startup Repair feature from one of the boot menus having access to Safe Mode.  What success with Startup Repair?  If that, too, runs into a fatal stop (the affected File and cause of crash should be readable when the BSOD appears), a factory reinstall may be necessary.

(Carbonite® kept a ready backup of my documents, excepting Cakewalk® documents kept in C:\Cakewalk Projects rather than an appropriate subdirectory of C:\Users, when I had need for a Win 7 reinstall; more details available at the [Carbonite® public Website](http://www.carbonite.com/).)

And I am perfectly fine doing a Factory Reinstall...but cannot because my disk drive is broken, and my computer does not have a hidden partition for recovery. And I have Windows Vista.

---

### Post by Hertz381 on 2011-11-18
Anything anyone else can suggest?

---

### Post by Mark Phelps on 2011-11-19
> **Hertz381 said:**
> Anything anyone else can suggest?

You will need two things -- that you don't have:
1) Set of full restore disks
2) Working CD/DVD drive

The first you will have to obtain from the PC vendor.  Since you deleted the Recovery partition, they are under no obligation to provide you anything for free.  So, they will probably charge you for restore media -- but they usually charge a modest fee to cover shipping and handling.

If you're not willing to replace the CD/DVD drive, and if your PC can boot from USB, then you could try copying the restore media files to a USB stick -- but this will be considerable work and could be very difficult to do properly.  It would be a lot easier to simply replace the drive.

---

### Post by Hertz381 on 2011-11-19
> **Mark Phelps said:**
> You will need two things -- that you don't have:
1) Set of full restore disks
2) Working CD/DVD drive

The first you will have to obtain from the PC vendor.  Since you deleted the Recovery partition, they are under no obligation to provide you anything for free.  So, they will probably charge you for restore media -- but they usually charge a modest fee to cover shipping and handling.

If you're not willing to replace the CD/DVD drive, and if your PC can boot from USB, then you could try copying the restore media files to a USB stick -- but this will be considerable work and could be very difficult to do properly.  It would be a lot easier to simply replace the drive.

I didn't delete the partition, it didn't come with one. 

I have the full recovery CD's, but do not have the CD / DVD drive. I am unable to afford the Drive for about a month, so I think I should try doing it with the USB stick. Are there any tutorials you can point me towards that would tell me how to do this. 

Also, the recovery disk is actually 2 disks.

---

### Post by alphaamanitin on 2011-11-21
You are stuck.  The only thing I can think you can try is to find a non-cracked Windows Vista disk on a torrent site.  If your windows install came with the computer you need an OEM version.  This is not illegal, you are going to use your license key that you paid for when you bought your computer.  Then you need to do some google kung-fu and learn how to make a bootable USB drive using your .iso windows vista OEM you downloaded.  Last time I check unpacking a .iso with WinRAR to a USB drive will make it bootable (but I may have been using UEFI booting not BIOS), there are programs to make a bootable drive that I am talking about.  I do not know any on linux though.  After making that bootable USB drive follow the others' instructions.  

Or, you can find some on who will let you borrow a optical drive or some one who has a external optical drive.

AlphaA

---

### Post by Mark Phelps on 2011-11-21
> **Hertz381 said:**
> I didn't delete the partition, it didn't come with one. I have the full recovery CD's ... 
Yeah .. if they provide CDs, they do not also install a Recovery Partition.   Just know that using CDs, it could take a LONG time to do a restore -- HOURS is not uncommon.

>  Also, the recovery disk is actually 2 disks.
Problem is that the first CD is most likely bootable, thus the USB stick would have to be bootable, too. So, you would have to create a bootable USB stick and then copy the files from the CD to that stick.  Without a working Windows PC, I don't know how to tell you to make a bootable Windows USB stick.

---

