---
title: "Ubuntu 10.10 wont detct my flash drive"
date: 2011-01-05
forum: General Help
---

### Post by meddyuk on 2011-01-05
Hi there. I wondered if anyone could help. I've got 2 USB sticks/pen drives/flash drives (what ever you wanna call them) and neither of them are detected by Ubuntu 10.10, when placed in the front USB ports of my deskstation.

I have got other USB devices working from the ports on the rear of my deskstation. I know that the ports on the front of my deskstation do actually work, as i plugged my iphone in there to charge it and Ubuntu detected it. 

I also know that the USB storage sticks do work as they are working on my laptop.

I have run gconf edit and made sure that in apps/nautilus/preferences that auto mount is enabled, but to no avail.

Please help.

Meddy.

---

### Post by nothingspecial on 2011-01-05
After you plug them in type

```
sudo fdisk -l
```

and
```

dmesg | tail -n 20
```

Then post what they say back here.

---

### Post by meddyuk on 2011-01-06
[FONT=Arial][SIZE=3]ok typed sudo fdisk -l and got this response:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe02ae02a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         653     5242880   1b  Hidden W95 FAT32
/dev/sda2   *         653        4864    33827157    7  HPFS/NTFS

Disk /dev/sdb: 30.8 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc03f240a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1245     9999360   83  Linux
/dev/sdb2            1246        1370      999425    5  Extended
/dev/sdb3            1370        3739    19027968   83  Linux
/dev/sdb5            1246        1370      999424   82  Linux swap / Solaris

[/SIZE][/FONT]

---

### Post by meddyuk on 2011-01-06
[FONT=Arial][SIZE=2]after typing dmesg | tail -n 20 i got

[   23.873052] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   23.874148] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   24.196033] intel8x0_measure_ac97_clock: measured 54650 usecs (2629 samples)
[   24.196038] intel8x0: clocking to 48000
[   24.197947] usbcore: registered new interface driver ndiswrapper
[   24.249605] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.909400] agpgart-sis 0000:00:00.0: AGP 3.5 bridge
[   25.909424] agpgart-sis 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[   25.909434] agpgart-sis 0000:00:00.0: putting AGP V2 device into 4x mode
[   25.909494] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   56.200177] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   66.752020] wlan0: no IPv6 routers present
[ 2185.616038] usb 1-6: new high speed USB device using ehci_hcd and address 4
[ 2185.762047] hub 1-6:1.0: USB hub found
[ 2185.762221] hub 1-6:1.0: 1 port detected
[ 2186.032276] usb 1-6.1: new high speed USB device using ehci_hcd and address 5
[ 2574.541896] audit_printk_skb: 9 callbacks suppressed
[ 2574.541901] type=1400 audit(1294308316.674:15): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=2224 comm="apparmor_parser"
[ 2574.552227] type=1400 audit(1294308316.686:16): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=2224 comm="apparmor_parser"
[ 2574.667635] type=1400 audit(1294308316.798:17): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer" pid=2224 comm="apparmor_parser"
[/SIZE][/FONT]

---

### Post by meddyuk on 2011-01-06
[FONT=Arial][SIZE=2]Furthermore, at present i have 4 USB ports, 2 to the rear which occupy my USB mouse and a USB webcam, the two ports at the front, i have plugged my USB pen drive in one and the other is free.[/SIZE][/FONT]

---

### Post by MARP1961 on 2011-01-06
I had the same problem and read that ndiswrapper can cause problems with USB devices mounting and being recognised. Try this code in the terminal:

sudo apt-get install usbmount

I've not had a problem since.

---

### Post by meddyuk on 2011-01-06
[FONT=Arial][SIZE=2]Ok that seemed to have worked....i think.

I checked the /media folder and there are now 7 USB folders. I did briefly see my light flash on my pen drive when i put it in, however, there is nothing that comes up on the desktop when i plug it in and there is nothing in my computer?

Any ideas on how to access the pen drive now?[/SIZE][/FONT]

Meddy.

---

### Post by MARP1961 on 2011-01-06
No sorry I cannot help further,I'm quite new to Linux and don't understand how it worked for me, but it did! All my USBs now mount and show an icon on the desktop. You do seem to be slowly inching towards a solution though. Hopefully someone else can advise.

---

### Post by meddyuk on 2011-01-06
Hey Marp, looks like its finally working. I plugged them in and up popped USB 0 on my desktop and im able to access the word documents in there!

Thanks a lot mate. All i gotta do is work out how remove it safely.

---

### Post by MARP1961 on 2011-01-06
Excellent and well done! However, I must admit, I cannot get mine to unmount either and have just been pulling the usb drive out once I've closed any files I was working on.

---

### Post by EthioJOB on 2011-01-06
Doesn't right-clicking on the usb icon on the desktop and selecting either *_unmount_*, *_eject_* or *_safely remove drive_* work? If the usb shows up on the desktop then I think these right-click options would be present.

---

### Post by MARP1961 on 2011-01-06
Back to square one! I've just tried a usb flash drive for the first time since my supposed success yesterday and once again it will not mount. I've even repeated the install of 'usbmount' to no avail. Anyone know what is wrong? I'm going to temporarily deinstall my ndiswrapper Windows XP wi-fi driver.

---

### Post by MARP1961 on 2011-01-06
I've tried the above and no success. Time to do some more searching I think.

---

### Post by meddyuk on 2011-01-09
Well i thought it was fixed. I think its a bit hit and miss to be honest. Ive logged on today and put my drive in today and hey ho its not detected it.....there must be something afoot here in ubuntu!

Meddy.

---

### Post by meddyuk on 2011-01-09
I tried plugging in another device in the USB port underneath my flash drive and then both suddenly appeared. There must be a problem with it, so im going to file a bug.

---

### Post by Fremont_Cunningham on 2011-05-15
This is about automount of USB flash drives (sticks/pens, NOT external disk-drives). It is not about manual (fstab) maonthing - that can usually be made to work. 
It appears that there may be a recent bug in the usbmount application, which is migrating to many versions of UBUNTU. I presently have these problems on 10.10, 10.4 and 8.04 - ALL have the problem now! For sure USB-Flash automount and unmount used to work *fine* on my 8.04 system, but now I find it no longer works. The 8.04 system is receiving and installing updates, so is the 10.04 system (both 32-bit intel). The 10.10 install is brand new and on AMD-64. *ALL* have these problems. There are two:
1) FAT32 8Gig USB Flash stick is not mounted, never appears on desktop, but 64Meg FAT16 and 2Gig FAT16 *do* appear on desktop.
2) It is not possible to right-click and unmount via the desktop ico. And error message is displayed 'umount: /media/usb0 is not in the fstab (and you are not root)' As I understand it, these devices are temp-mounted and so are not expected to be in fstab.

The utility that deals with USB flash stick mounting is "usbmount". Google that for information. Although it is installed it has no man page.
There are  hints on the web that usbmount has some bug in v0.0.2 (which is what UBUNTU is distributing, and that some bugs were fixed in 0.0.21.

It may be that the above problems are being caused by bugs in some other necessary support area, I do not know enough to determine that.

I can supply system log snippets for those who have the skill to research this problem.

---

### Post by coffeecat on 2011-05-30
> **Fremont_Cunningham said:**
> It appears that there may be a recent bug in the usbmount application, which is migrating to many versions of UBUNTU.

It's not so much that there is a bug in usbmount, more that you should not be using it in a desktop version of Ubuntu. From the usbmount package description:

> USBmount is intended as a lightweight solution [B]which is independent of
a desktop environment.[/B] There are many people falling foul of this application. The fix is easy: uninstall it. Then the more than adequate USB automouting functionality which has been built into desktop (GUI) versions of Ubuntu for some years will work properly without being compromised by an application intended for use on a GUI-less server system.

---

### Post by dandnsmith on 2011-05-30
Just checked in package manager, on a 10.04 with usb mounting working - I don't have usbmount installed

---

### Post by coffeecat on 2011-05-30
> **dandnsmith said:**
> Just checked in package manager, on a 10.04 with usb mounting working - I don't have usbmount installed

No, indeed. It doesn't come with a default install of Ubuntu. It's in the Universe repository anyway, which means it is not an "official" Ubuntu package. It's causing so much grief for unsuspecting and often inexperienced users that I'm thinking of raising a bug on launchpad requesting that a huge health warning be added to the beginning of the package description. The quote  I posted comes near the end and is just not clear enough. Not that everyone reads package descriptions before installing stuff from the repos anyway. :( 

What puzzles me is how so many people find it.

---

### Post by Fremont_Cunningham on 2011-05-31
Ubuntu 10.10, AMD64 system. Update:
After some recent system update the FAT16 flash drives started automounting again. The FAT32 drive still fails.
On reading the useful post by coffeecat I uninstalled 'usbmount', rebooted and tried again. Result: FAT16 flash drives auto-mount fine. FAT32 drive still fails.
I suggest that people install usbmount in a desperate attempt to get these new(ish) FAT32 drives to mount. Perhaps the real cure is to get the base UBUNTU istall to deal with FAT32 drives? (They work instantly without any problem in Windows XP.)

Disk Utility lists the device as having Partition Type W95 FAT32 (LBA)(0x0c)
Is this as-yet unsupported by linux? Is it possible to reformat the flash drive to something that is supported? Again - on the web I find many postings from linux users being unable to mount FAT32.

I can post dumps from logs and probes etc. to help work on this problem.

---

### Post by coffeecat on 2011-05-31
@Fremont_Cunningham, I have been using Ubuntu on a variety of machines since about 2006. I have never, EVER had problems automounting FAT32-formatted USB drives. FAT32 is fully supported.

---

### Post by Fremont_Cunningham on 2011-05-31
@Coffeecat - I am very pleased for you :)
The discussion here is about an ongoing problem where FAT32 USB flash drive does not auto-mount, and suggestions to fix that problem.

---

### Post by coffeecat on 2011-05-31
> **Fremont_Cunningham said:**
> @Coffeecat - I am very pleased for you :)
The discussion here is about an ongoing problem where FAT32 USB flash drive does not auto-mount, and suggestions to fix that problem.

I was responding to this:

> **Fremont_Cunningham said:**
> I suggest that people install usbmount in a desperate attempt to get these new(ish) FAT32 drives to mount.  Perhaps the real cure is to get the base UBUNTU istall to deal with FAT32 drives? (They work instantly without any problem in Windows XP.)

There is no cure to be made. The "base install of Ubuntu" does indeed deal with FAT32 filesystems.  If you have a FAT32 drive that doesn't automount in Ubuntu but does in Windows, it certainly needs investigating, but you can't assume that Ubuntu is lacking in this respect.

One thing I would look at is the filesystem itself. Windows is fairly tolerant of a corrupted filesystem and will mount it - which is a bad thing, imo. If Ubuntu detects a corrupted FAT32 filesystem it will not mount it in order to protect it from further damage. So it would be a good idea to do a chkdsk in Windows on the drive in question.

---

### Post by Fremont_Cunningham on 2011-06-06
chkdsk in Windows did not seem to show anything odd about the FAT32 8Gig USB Flash stick, result '.. found no problems'. Eventually out of frustration I ran 'format' for this USB Flash stick on the windows machine. (For other readers with this problem SAVE ANY CONTENTS ELSEWHERE FIRST!). After running FAT32 format with default sector size (no other options were possible) windows chkdisk result appeared unchanged. I then moved the Flash stick to the UBUNTU machine, and voila! UBUNTU auto-mounted it! So - it appears that the factory formatting does have some feature (or lacks) that windows does not care about, but UBUNTU does.
I tested a second virgin USB flash stick -same make/model. UBUNTU would not auto-mount it, but System/Administration/DiskUtility did 'see' a 'General USB Flask Disk'. On selecting that the Volume Usage entry showed as '-', whereas the one that had been formatted in windows showed 'Filesystem'.
I then selected the 'Format Volume' option, Type 'FAT'. After it had run the Volume Usage entry showed as 'Filesystem'. After remove and connect of the USB Flash stick UBUNTU auto-mounted it. 
I have tested both drives by writing a file on one system and reading on the other system (Windows XP & UBUNTU 10.10 Maverick) and bot seem to work ok.

For those reading this in the future, the 8G USB Flask stick is a CANDY drive by 'Team Group' model SC901. lsusb shows the device as
ID 090c:1000 Feiya Technology Corp. Flash Drive

---

### Post by coffeecat on 2011-06-07
Thanks for posting that information. Useful to know that some pre-formatted USB flash drives are giving problems - if I'm reading you correctly. Factory formats don't usually last long in this household (intentionally! :)) which is perhaps why I hadn't seen this.

---

