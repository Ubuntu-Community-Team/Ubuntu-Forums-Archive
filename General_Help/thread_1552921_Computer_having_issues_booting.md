---
title: "Computer having issues booting"
date: 2010-08-14
forum: General Help
---

### Post by Polis4rule on 2010-08-14
I come to you with desperate help needed. A week before heading off to college, my computer is having some serious problems. It is a Sony E series, and it probably has to do with the fact that I'm a bonehead (or just better than the general populace) and installed Ubuntu along side Windows on the comp. 

Anyway, I now cannot boot into Windows at all. If I try to turn on the computer without my Windows recovery CD in the tray, it displays an error message: 

"Error: hd0,5 out of disk 
<grub> (or something to that effect)" 

Well, it says something about grub. Now I'm desperate. I'm fairly computer literate, but I'm not some Linux superuser. All I have done on the Linux side of my computer is install update. What can I do about this? Preferably, I just want to get rid of Ubuntu as even though it is really nice and I do like it, I'd prefer my computer to just simply boot into Windows. 

Thanks in advance.

---

### Post by Polis4rule on 2010-08-14
Specifications

Model: Sony VPCEB
Processor: i5-520M
RAM: 4 gigs
Video: ATI Mobility Radeon HD 5470 GPU
Hard Drive: 500 GB

Preferably, I would just like to solve this issue and get functionality back to the laptop (as I have some semi-important documents on the Windows side).

Thanks in advance.

---

### Post by Rubi1200 on 2010-08-14
Do you have an Ubuntu CD?

If yes, boot the computer with it and choose to try in live mode.

Click on the link at the bottom of my post and follow the instructions there.

Post the results back here.

This will help us get a better view of your setup and make offering solutions easier.

Thanks.

---

### Post by Polis4rule on 2010-08-14
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sda1     ?             0            -1                   Unknown
/dev/sda2     ?             0            -1                   Unknown
/dev/sda3     ?             0            -1                   Unknown
/dev/sda4     ?             0            -1                   Unknown


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mmcblk0p1   7060-F8B4                              vfat       READYBOOST                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda


Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]

Posting this, but I know that this isn't suppose to happen, right? And I think when I installed Ubuntu, I might have installed over the Windows partition. Everything was perfectly fine until yesterday, but I think it was the latest updates that I installed for Ubuntu that might've messed up everything (system started to slow down and act funny). I'd still like to recover my Windows settings and files, but it looks like something is pretty messed up. 

I was told by some people on Gizmodo/Lifehacker (when I also asked them for help) to refer to this thread here for possible help. [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Polis4rule on 2010-08-14
I should say that I didn't use the Windows Installer when installing Ubuntu, as I installed Ubuntu before on other computers in the same fashion and have not had any problems.

---

### Post by -Duvel- on 2010-08-14
you can also use ms-sys to restore the vista bootloader
[ms-sys.sourceforge.net]("http://ms-sys.sourceforge.net")
you'll have to download, unpack and compile this after you booted from the live cd (iirc you should also install gettext for ms-sys to compile -  apt-get install gettext )

---

### Post by Polis4rule on 2010-08-14
I have Win 7 on my laptop, I assume that there is a similar file for Win 7?

---

### Post by Polis4rule on 2010-08-14
Sorry for the double post, but would my issues be solved fixing GRUB?

If all else fails, would I be able to install Windows via the recovery disks from an empty drive?

---

### Post by Neobuntu on 2010-08-14
In the course of my troubles, I saw restoring Windows on the menu directions, for GRUB 2 (grub-pc), Google that.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

...might do it.

---

### Post by Polis4rule on 2010-08-14
It appears as though my computer is not registering that I have Win 7 or Ubuntu on my hard drive, and the Live CD won't let me mount the drive either. 

I'm pretty much in tears now, as the standard procedures seem to not work and my computer can't even view the hard drive. I don't have a full copy of Windows either, only the recovery disks.

---

### Post by Quackers on 2010-08-14
Using the recovery discs should bring your Windows system back to its brand new state. It may be that it's the only option you have. It will take about 45 mins to an hour to run and then you will have updates to run, which could take some time. It looks like all your data is gone I'm afraid.
Hang on a while and see if somebody comes up with a better idea.
Good luck.

---

### Post by Rubi1200 on 2010-08-14
You might want to have a go at using testdisk to see if there is anything to recover.

But, I suspect Quackers might be right about your data and recovery options.

[https://help.ubuntu.com/community/DataRecovery#Testdisk](https://help.ubuntu.com/community/DataRecovery#Testdisk)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Good luck!

:)

---

### Post by Polis4rule on 2010-08-14
> **Rubi1200 said:**
> You might want to have a go at using testdisk to see if there is anything to recover.

But, I suspect Quackers might be right about your data and recovery options.

[https://help.ubuntu.com/community/DataRecovery#Testdisk](https://help.ubuntu.com/community/DataRecovery#Testdisk)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Good luck!

:)

Yeah, I tried to get testdisk to work, but it wouldn't do anything. Thank you though.

> **Quackers said:**
> Using the recovery discs should bring your Windows system back to its brand new state. It may be that it's the only option you have. It will take about 45 mins to an hour to run and then you will have updates to run, which could take some time. It looks like all your data is gone I'm afraid.
Hang on a while and see if somebody comes up with a better idea.
Good luck.

Thanks for the response. How would I be able to reinstall via the recovery disks? I can boot up via the Live CD, so I know my system can boot up from a DVD, but putting the recovery disk in my system only brings up GRUB.

---

### Post by Quackers on 2010-08-14
On booting with the dvd in the drive you should get a prompt to press any key to boot from dvd. It may be that you will need to enter the bios and select the dvd drive as the first bootable device, then the hard drive as second device. To enter bios you will need to keep tapping a key during the boot process. The key is different for different motherboards. Often it will be the F11 or F12 or del.
You need to find out from your manual which key to press.
Whilst you are in the manual, try looking for recovery options. It may well be that your system has a recovery partition (but that may or may not have been damaged) which will be accessible by pressing a different key during boot.

---

