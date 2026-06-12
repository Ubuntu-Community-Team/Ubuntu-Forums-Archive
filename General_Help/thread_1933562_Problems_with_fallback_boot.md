---
title: "Problems with fallback boot"
date: 2012-02-29
forum: General Help
---

### Post by Bardobrave on 2012-02-29
Hi all.

I have an environment with two hard disks, one has a windows 7 installed and another one has an Ubuntu 11.10, my system usually boots from grub and let me choose wich system to initiate.

Now my ubuntu disk is starting to fail, often I'm unable to boot due to problems in the disk (he's not recognized) and I'm prompted to grub_rescue> with a hd1 is out of disk message.

I thought... well.. it's easy, let's change hard disks boot order on BIOS and Windows 7 will boot by default until I buy a new disk and recover linux system, but it seems I was wrong, even when I state on BIOS that windows hard disk should boot first, the message on grub_rescue appears and the system halts.

Now I boot from Hirens boot CD, where I have an option to load directly windows, but I supose that there should be a solution to this.

Any suggestions?
Thanks in advance.

---

### Post by 23dornot23d on 2012-02-29
Once you have a faulty Hard Drive strange things can happen ... mainly lock-ups and corrupt data.

My advice is to remove the faulty drive or disconnect it ...... until a time that you get the new drive to replace it ......

I have found the quickest cheapest and easiest method for me is to go out and buy a USB
hard drive ..... 500 Gig Seagates I find to be the best and quickest .... for my use.

( at the time you need to get the the data off the failing drive - reconnect it - then the USB can be plugged in - as much Data as you can get off of the failing drive .... then remove it ...... for good and use the USB after that ..... as they are more portable and very handy to have )

---

### Post by Mark Phelps on 2012-02-29
From what you say, it looks like GRUB is installed on your Win7 drive.

You can fix this by doing the following:
1) Go to the link below and use the info to download the Boot-Repair ISO and burn that to CD.
2) Boot the PC from this CD -- but have only the Win7 drive connected
3) Use the CD to repair the Win7 boot function.
4) Remove the CD and boot from the Win7 drive ... that should work now.

Link:  [http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by Bardobrave on 2012-03-01
@23dornot23d: 
I've tried unplugging the faulty hard disk, but then the grub_rescue> shows a different message, stating that don't exist a device on the system (with a long device number wich I supose that represents the missing hd).

@Mark Phelps:
It seems a good advice, I'll try it. I wonder how grub could got installed on windows drive instead of on the drive where ubuntu was installed.

---

### Post by Mark Phelps on 2012-03-01
> **Bardobrave said:**
> @Mark Phelps:
It seems a good advice, I'll try it. I wonder how grub could got installed on windows drive instead of on the drive where ubuntu was installed.

Don't know -- since you apparently had the Win7 drive disconnected when you installed Ubuntu.  But if GRUB was not there, when you have only the Win7 drive connected, you would not see any GRUB messages.

---

### Post by Bardobrave on 2012-03-01
> **Mark Phelps said:**
> Don't know -- since you apparently had the Win7 drive disconnected when you installed Ubuntu.  But if GRUB was not there, when you have only the Win7 drive connected, you would not see any GRUB messages.

Not exactly. The computer came with a hard disk with win7 installed. Later I plugged another disk from my previous machine where I had a NTFS partition with data. Finally I installed Ubuntu on the "data" hard disk (on a new partition besides the NTFS one).

So when Ubuntu was installed both disks were present.

---

### Post by 23dornot23d on 2012-03-01
> 
@23dornot23d: 
I've tried unplugging the faulty hard disk, but then the grub_rescue>  shows a different message, stating that don't exist a device on the  system (with a long device number wich I supose that represents the  missing hd).

Grub is possibly on the first drive ..... but to get the information off the drive - try to get a USB hard drive and copy what you really need.

Because once hard drives die completely which usually is not long after symptoms start appearing ..... you then end up with no options to recover data.

If you run this script ... it will give people more to work on - as it will give detailed information about your disks and how they boot up .....

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please post back the results after running it ..... ty

---

### Post by Bardobrave on 2012-03-01
> **23dornot23d said:**
> Grub is possibly on the first drive ..... but to get the information off the drive - try to get a USB hard drive and copy what you really need.

Because once hard drives die completely which usually is not long after symptoms start appearing ..... you then end up with no options to recover data.

If you run this script ... it will give people more to work on - as it will give detailed information about your disks and how they boot up .....

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please post back the results after running it ..... ty

Ok, I'll try to post it, although is possible that I cannot do it until tomorrow in the afternoon. Here it is, however, the result of the bcdedit of the windows 7 disk, maybe it helps you to clarify the situation:


```

Windows Boot Manager
----------------------------------
Identifier             {bootmgr}
device                  partition=\Device\HarddiskVolume1
description             Windows Boot Manager
locale                  es-ES
inherit                 {globalsettings}
default                 {current}
resumeobject            {f8e8a11e-a1ae-11e0-873e-cce75c7a883e}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30

Windows boot loader
-----------------------------
Identifier             {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  es-ES
inherit                 {bootloadersettings}
recoverysequence        {f8e8a120-a1ae-11e0-873e-cce75c7a883e}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {f8e8a11e-a1ae-11e0-873e-cce75c7a883e}
nx                      OptIn


```

As far as I am able to understand, seems that windows is booting to a manager (probably grub) positioned on the other disk. I wonder if this would solve by simply removing the windows boot manager entry on that file (tomorrow with time and tanquility maybe I backup the file and try it)

I'm not sure, but I think that this {f8e8a11e-a1ae-11e0-873e-cce75c7a883e} is the device that grub_rescue> states that is missing when the ubuntu disk is unplugged.

Does this throws any light over the problem for you? Any further suggestion is always welcomed.

---

### Post by 23dornot23d on 2012-03-01
I will wait for the script information .... the windows information does not tell me anything
about the Ubuntu partitions or grub ......

There are ways to set grub up on the first drive or even on USB flash drives ..... to solve
this situation .....

We will learn more once the script has been run .... it creates a results.txt file and its just a case of cutting and pasting the information once it has run.

Its purely to find things out - and does nothing but look at the drives for the boot information and reports back in a way that can easily be understood and allows others to
track down any problems and also ways to set the drive up so that it will boot ok.

Cheers for the feedback though , windows info does not show me what we need though.

---

### Post by Bardobrave on 2012-03-02
Ok, this is the response for the boot_info_script:

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 9 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,953,521,663 1,953,314,816   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4ECC4C1CCC4C0127                       ntfs       Reservado para el sistema
/dev/sda2        5CC85026C85000A6                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

Reading it I think that grub is installed on the ghost boot partition of windows 7, and somewhat as it's unable to find my old disk it's unable to boot.

I've found a windows program to edit and repair windows boot system (I'm more a win boy than a linuxer yet), but I'd like to hear your opinion and suggestions before starting.

---

### Post by 23dornot23d on 2012-03-02
Well the boot loader is on the main drive .... and if you can set it to boot up for 
windows - then that is probably the best choice here .....

as the second drive is not visible ...... the thing to do then is when you get a
replacement drive ...... put grub on sdb and then switch using the BIOS to
boot from sdb ...... for Ubuntu .... 

( this is of course to keep it separate from the windows drive )

The Fact that drive sdb is not visible on here - leaves few options .... as there is no 
sign of Ubuntu or Linux .....

> 
Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of      the same hard drive for core.img. core.img is at this location and looks      in partition 9 for .


---

### Post by Bardobrave on 2012-03-03
It was a bit strange when I installed ubuntu, as the installer didn't allow me to install ubuntu on a new partition on sda (I wanted to have sda as a dual system hd and sdb as data hd with an NTFS partition), so I installed it on sdb but... somehow... grub got installed on sda boot partition and now I have this mess :confused:

I think I'll try to repair the windows boot from bcd edit and try to install ubuntu later on the same drive (on a different partition, of course).

Thank you for your help.:)

---

### Post by Bardobrave on 2012-03-04
Ok, finally, after screwing up things with EasyBCD and letting my windows hd unbootable I was able to fix things up booting from windows install dvd and choosing to repair system.

Thank you all for your help.

---

### Post by 23dornot23d on 2012-03-04
Glad you got it working ok .....

With Windows .... its often best to keep things separate.

Its not that Ubuntu or Linux does not try its hardest to cater for Windows.

Best of luck in the Future ....

---

