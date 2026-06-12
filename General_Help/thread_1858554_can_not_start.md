---
title: "can not start"
date: 2011-10-12
forum: General Help
---

### Post by giobasi on 2011-10-12
installed ubuntu 11.10 with windows 7 and I see this  

[http://www.youtube.com/watch?v=R_YhhqChfjA](http://www.youtube.com/watch?v=R_YhhqChfjA)

:confused:

---

### Post by TeoBigusGeekus on 2011-10-12
Is this a wubi or a normal installation?
When does this happen, i.e. before of after grub (bootloader)?

---

### Post by giobasi on 2011-10-12
> **TeoBigusGeekus said:**
> Is this a wubi or a normal installation?
When does this happen, i.e. before of after grub (bootloader)?

wubi I try normal but its was worse, only black screen  

"When does this happen, i.e. before of after grub (bootloader)?" - after install i try start ubuntu , they was windows 7 and ubuntu , chose ubuntu,   This is the answer to your question?

---

### Post by oldos2er on 2011-10-12
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by TeoBigusGeekus on 2011-10-12
> **giobasi said:**
> wubi I try normal but its was worse, only black screen  

"When does this happen, i.e. before of after grub (bootloader)?" - after install i try start ubuntu , they was windows 7 and ubuntu , chose ubuntu,   This is the answer to your question?

I've never tried wubi, so I can't tell you.
Have you tried the installation media for defects?
Did the live session work?

---

### Post by giobasi on 2011-10-12
> **TeoBigusGeekus said:**
> I've never tried wubi, so I can't tell you.
Have you tried the installation media for defects?
Did the live session work?

LiveCD? yes.

no , I have not installed anu media for defects, 

I try wubi Because  I thought it was easier, before wubi use,I normally install from CD,  But  was not Ubuntu to select, none windows on startup, I saw only black screen   than I install grub with liveCD , no Results, than install windows and wubi

---

### Post by realstarman on 2011-10-13
I have a similar issue ([http://http://ubuntuforums.org/showthread.php?t=1858270]("http://http://ubuntuforums.org/showthread.php?t=1858270")) but manage to boot by switching acpi off.
Have you tried this?
You can set this temporarily in GRUB (the boot loader) by selecting your normal Ubuntu boot entry and pressing "e".
In the Following screen, find the entry that starts with "linux /boot....". Then hit the "end" key and add " acpi=off". Then press F10. The system will boot once with this setting.

---

### Post by giobasi on 2011-10-13
> **realstarman said:**
> I have a similar issue ([http://http://ubuntuforums.org/showthread.php?t=1858270]("http://http://ubuntuforums.org/showthread.php?t=1858270")) but manage to boot by switching acpi off.
Have you tried this?
You can set this temporarily in GRUB (the boot loader) by selecting your normal Ubuntu boot entry and pressing "e".
In the Following screen, find the entry that starts with "linux /boot....". Then hit the "end" key and add " acpi=off". Then press F10. The system will boot once with this setting.

I already uninstalled Ubuntu  and Can I do this "acpi=off" during the installation with wubi, I know where is the  acpi=off when installing with CD (f6), but  I do not want install with CD, Because then I cannot start windows (Ubuntu is switched on automatically, it does not appear  elected Menu)

---

### Post by Mark Phelps on 2011-10-13
BEFORE you do anything else, do yourself a favor and use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader.

---

### Post by giobasi on 2011-10-13
> **Mark Phelps said:**
> BEFORE you do anything else, do yourself a favor and use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader.
ok

---

### Post by giobasi on 2011-10-13
[B]its my PC, I have read some bios problems , is my bios an PC good for ubuntu?

BIOS Properties	
Vendor	American Megatrends Inc.
Version	0103
Release Date	11/04/2005
Size	512 KB
Boot Devices	Floppy Disk, Hard Disk, CD-ROM, ATAPI ZIP, LS-120
Capabilities	Flash BIOS, Shadow BIOS, Selectable Boot, EDD, BBS
Supported Standards	DMI, APM, ACPI, ESCD, PnP
Expansion Capabilities	ISA, PCI, AGP, USB[/B]

[B]
    


--------[ Summary ]-----------------------------------------------------------------------------------------------------

    Computer:
      Computer Type                                     ACPI x64-based PC
      Operating System                                  Microsoft Windows 7 Ultimate
      OS Service Pack                                   -
      Internet Explorer                                 9.0.8112.16421
      DirectX                                           DirectX 11.0
      Computer Name                                     BASILA-PC
      User Name                                         basila
      Logon Domain                                      basila-PC
      Date / Time                                       2011-10-13 / 18:08

    Motherboard:
      CPU Type                                          Intel Pentium 4 531, 3000 MHz (15 x 200)
      Motherboard Name                                  Asus P5AD2-E  (3 PCI, 2 PCI-E x1, 1 PCI-E x16, 4 DDR2 DIMM, Audio, Gigabit LAN)
      Motherboard Chipset                               Intel Alderwood i925XE
      System Memory                                     1536 MB  (DDR2 SDRAM)
      DIMM1: A-Data                                     512 MB DDR2-667 DDR2 SDRAM  (5-5-5-15 @ 333 MHz)  (4-4-4-12 @ 266 MHz)  (3-3-3-9 @ 200 MHz)
      DIMM3: Crucial RM12864AA800.8FH                   1 GB DDR2-800 DDR2 SDRAM  (6-6-6-18 @ 400 MHz)  (5-5-5-15 @ 333 MHz)  (4-4-4-12 @ 266 MHz)
      BIOS Type                                         AMI (11/04/05)
      Communication Port                                Communications Port (COM1)
      Communication Port                                ECP Printer Port (LPT1)

    Display:
      Video Adapter                                     Radeon X300/X550/X1050 Series (Microsoft Corporation - WDDM)  (256 MB)
      Video Adapter                                     Radeon X300/X550/X1050 Series (Microsoft Corporation - WDDM)  (256 MB)
      3D Accelerator                                    ATI Radeon X550 (RV370)
      Monitor                                           LG Flatron ez T707B  [17" CRT]  (1512142511)

    Multimedia:
      Audio Adapter                                     C-Media CMI9880 @ Intel 82801FB ICH6 - High Definition Audio Controller [B-2]

    Storage:
      IDE Controller                                    Intel(R) 82801FB Ultra ATA Storage Controllers - 2652
      IDE Controller                                    Intel(R) 82801FB/FBM Ultra ATA Storage Controllers - 266F
      Disk Drive                                        MAXTOR STM3320820AS ATA Device  (320 GB, 7200 RPM, SATA-II)
      Optical Drive                                     TSSTcorp CD/DVDW SH-W163A ATA Device  (DVD+R9:8x, DVD-R9:4x, DVD+RW:16x/8x, DVD-RW:16x/6x, DVD-ROM:16x, CD:48x/32x/40x DVD+RW/DVD-RW)
      SMART Hard Disks Status                           OK

    Partitions:
      C: (NTFS)                                         79901 MB (30501 MB free)
      D: (NTFS)                                         52831 MB (45438 MB free)
      E: (NTFS)                                         79999 MB (79907 MB free)
      F: (NTFS)                                         92397 MB (92305 MB free)
      G: (NTFS)                                         99 MB (83 MB free)
      Total Size                                        298.1 GB (242.4 GB free)

[/B]

---

### Post by giobasi on 2011-10-18
up

---

### Post by bcbc on 2011-10-19
> **giobasi said:**
> I already uninstalled Ubuntu  and Can I do this "acpi=off" during the installation with wubi, I know where is the  acpi=off when installing with CD (f6), but  I do not want install with CD, Because then I cannot start windows (Ubuntu is switched on automatically, it does not appear  elected Menu)

See this: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Wubi-specific for the first boot is post [#8]("http://ubuntuforums.org/showpost.php?p=10089820&postcount=8").

---

### Post by giobasi on 2011-10-20
> **bcbc said:**
> See this: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Wubi-specific for the first boot is post [#8]("http://ubuntuforums.org/showpost.php?p=10089820&postcount=8").

loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
search --set=diskroot -f -n /ubuntu/disks/root.disk
probe --set=diskuuid -u $diskroot
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk preseed/file=/ubuntu/install/preseed.cfg wubi-diskimage ro quiet splash nomodeset
initrd /initrd.img
boot

I do this, than reboot and auto starts same, than reboot and press ESC many time and see this [IMG]http://ubuntuforums.org/attachment.php?attachmentid=204928&stc=1&d=1319117457[/IMG]

and loading ubuntu :), but after reboot problem  return :(

---

### Post by bcbc on 2011-10-20
> **giobasi said:**
> 

and loading ubuntu :), but after reboot problem  return :(

> **bcbc said:**
> Wubi overrides are identical to what you have there - once it is installed. 

To override on the initial install is different and to complicate things, since Ubuntu 11.10 there are two distinct methods to install with Wubi.
...
[B]In the same way as the non-wubi install, the override is only in place for as long as the installation process. After the unattended install the computer reboots, and the next time you select Ubuntu you get a normal looking grub menu (looks identical to normal installs at a high level) and you apply the override as you described in the first post.
[/B]
Once booted, install drivers, or override using /etc/default/grub



I'll make this a little clearer under the 'method 2' post since I skipped the paragraph in bold, and only added the final paragraph. 

So, now that you've done the initial install, you need to review post #1 to see how to override it and then make permanent changes to either install a driver or make the kernel boot option stick.

---

### Post by giobasi on 2011-10-20
> **bcbc said:**
> I'll make this a little clearer under the 'method 2' post since I skipped the paragraph in bold, and only added the final paragraph. 

So, now that you've done the initial install, you need to review post #1 to see how to override it and then make permanent changes to either install a driver or make the kernel boot option stick.

thx ,  this?  [http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

so which line is solution ?

and I use LiveCD to boot installed wubi ubuntu 11.10. I restart PC, than press F8 , chose CD-DVD,  than F6, than  I chose boot from first disk , and than press ESC, this is only way to boot ubuntu on my PC

---

### Post by giobasi on 2011-10-21
100% CPU usage , why?

---

### Post by giobasi on 2011-10-24
yesss solved, I delete this 100 mb partition, and than uninstall /install new wubi 11.10,after instal there was not boot entry for ubuntu in windwos loader and I add from command prompt:


bcdedit /create /d ubuntu /application BOOTSECTOR

You’ll need to replace {ID} by the actual returned identifier. An example of {ID} is {d7294d4e-9837-11de-99ac-f3f3a79e3e93}.

bcdedit /set {ID} device partition=E:

The path to ubuntu\winboot\wubildr.mbr file:

bcdedit /set {ID} path \ubuntu\winboot\wubildr.mbr

An entry to the displayed menu at boot time:

bcdedit /displayorder {ID} /addlast

---

