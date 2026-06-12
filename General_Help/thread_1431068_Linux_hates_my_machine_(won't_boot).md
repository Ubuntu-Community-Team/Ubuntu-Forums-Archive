---
title: "Linux hates my machine (won't boot)"
date: 2010-03-16
forum: General Help
---

### Post by serosis on 2010-03-16
I've tried every possible boot variant that is humanly possible and my machine for the life of it will not boot into linux.

Ubuntu i386 likes to freeze right at the Logo and progress bar
Ubuntu x64 gets all the way to gnome, but it's only a desktop and cursor
gParted loves to spout "NTFS Volume version 3.1" while telling me it can't find its own files to load from.
Tried both CD and DVD media and varying levels of speed gives the same results.

Trying any of it from a LiveUSB boot gives me "Boot Error".

Something I noticed is that my drive itself tends to stop reading the CD/DVD at the point of hang. No spin-up and my HDD light flickers at 1 sec intervals.

Any clues?

---

### Post by Grenage on 2010-03-16
If the problem occurs at the same point in the boot, the drive is likely fine.  It will stop reading because Ubuntu has hanged, and needs no further data.

Are you able to press Ctrl-Alt-F8 and see what is being loaded?  I'm not very experienced in diagnosing such things.

---

### Post by serosis on 2010-03-16
> **Grenage said:**
> If the problem occurs at the same point in the boot, the drive is likely fine.  It will stop reading because Ubuntu has hanged, and needs no further data.

Are you able to press Ctrl-Alt-F8 and see what is being loaded?  I'm not very experienced in diagnosing such things.

It gets to the point to where the keyboard will not respond at all.

Except on gParted, CTRL+ALT+DEL works at restarting my system.

---

### Post by Grenage on 2010-03-16
Is there a boot option that has ACPI disabled, does that make any difference?

---

### Post by serosis on 2010-03-16
> **Grenage said:**
> Is there a boot option that has ACPI disabled, does that make any difference?

makes no difference whatsoever

---

### Post by Grenage on 2010-03-16
Can you post a full list of your hardware?  There is a good chance that if any of it lacks basic support, someone will recognise it.

---

### Post by serosis on 2010-03-16
Here's an Everest Summary:
```
    Computer:
      Computer Type                                     ACPI Uniprocessor PC
      Operating System                                  Microsoft Windows XP Professional
      OS Service Pack                                   Service Pack 3
      Internet Explorer                                 8.0.6001.18702 (IE 8.0)
      DirectX                                           4.09.00.0904 (DirectX 9.0c)
      Computer Name                                     MAIN
      User Name                                         Serosis
      Logon Domain                                      MAIN
      Date / Time                                       2010-03-16 / 10:52

    Motherboard:
      CPU Type                                          AMD Athlon 64, 2200 MHz (11 x 200) 3500+
      Motherboard Name                                  MSI MS-7184
      Motherboard Chipset                               ATI Radeon Xpress 200/1100/1150, AMD Hammer
      System Memory                                     2048 MB  (PC3200 DDR SDRAM)
      DIMM1: Kingston K                                 1 GB PC3200 DDR SDRAM  (3.0-3-3-8 @ 200 MHz)  (2.5-3-3-7 @ 166 MHz)
      DIMM2: Kingston K                                 1 GB PC3200 DDR SDRAM  (3.0-3-3-8 @ 200 MHz)  (2.5-3-3-7 @ 166 MHz)
      BIOS Type                                         Award (08/19/05)
      Communication Port                                Printer Port (LPT1)

    Display:
      Video Adapter                                     NVIDIA GeForce 9400 GT  (512 MB)
      3D Accelerator                                    nVIDIA GeForce 9400 GT
      Monitor                                           KDS Visual Sensation VS-195e  [19" CRT]  (BAA21025679)

    Multimedia:
      Audio Adapter                                     Realtek ALC658 @ ATI SB400 - AC'97 Audio Controller

    Storage:
      IDE Controller                                    Standard Dual Channel PCI IDE Controller
      IDE Controller                                    Standard Dual Channel PCI IDE Controller
      IDE Controller                                    Standard Dual Channel PCI IDE Controller
      Storage Controller                                ABBD70UG IDE Controller
      Disk Drive                                        ST3100011A  (100 GB, 7200 RPM, Ultra-ATA/100)
      Disk Drive                                        ST3400832A  (400 GB, 7200 RPM, Ultra-ATA/100)
      Optical Drive                                     MAD DOG LS-DVDRW TSH652M  (DVD+R9:8x, DVD-R9:8x, DVD+RW:18x/8x, DVD-RW:18x/6x, DVD-RAM:12x, DVD-ROM:16x, CD:48x/32x/48x DVD+RW/DVD-RW/DVD-RAM)
      SMART Hard Disks Status                           OK

    Partitions:
      C: (NTFS)                                         95393 MB (84764 MB free)
      D: (NTFS)                                         372.6 GB (31.3 GB free)
      Total Size                                        465.8 GB (114.1 GB free)

    Input:
      Keyboard                                          HID Keyboard Device
      Mouse                                             HID-compliant mouse

    Network:
      Primary IP Address                                255.255.255.1
      Primary MAC Address                               00-00-00-00-00-00
      Network Adapter                                   Realtek RTL8139 Family PCI Fast Ethernet NIC  (192.168.1.2)
      Network Adapter                                   VMware Virtual Ethernet Adapter for VMnet1  (192.168.22.1)
      Network Adapter                                   VMware Virtual Ethernet Adapter for VMnet8  (192.168.135.1)

    Peripherals:
      FireWire Controller                               VIA VT6307 Fire IIM IEEE1394 Host Controller (PHY: VIA VT6307)
      USB1 Controller                                   ATI SB400 - USB Controller
      USB1 Controller                                   ATI SB400 - USB Controller
      USB2 Controller                                   ATI SB400 - USB 2.0 Controller
      USB Device                                        Generic USB Hub
      USB Device                                        USB Composite Device
      USB Device                                        USB Human Interface Device
      USB Device                                        USB Human Interface Device
      USB Device                                        USB Human Interface Device

    DMI:
      DMI BIOS Vendor                                   Phoenix Technologies, LTD
      DMI BIOS Version                                  6.00 PG
      DMI System Manufacturer                           Gateway
      DMI System Product                                
      DMI System Version                                
      DMI System Serial Number                          
      DMI Motherboard Manufacturer                      MICRO-STAR
      DMI Motherboard Product                           MS-7184
      DMI Motherboard Version                           
      DMI Motherboard Serial Number                     6910902053
      DMI Chassis Manufacturer                          
      DMI Chassis Version                               
      DMI Chassis Serial Number                         
      DMI Chassis Asset Tag                             
      DMI Chassis Type                                  Desktop Case
      DMI Total / Free Memory Sockets                   4 / 2
```

EDIT:

I'm gonna see what happens with Wubi.

EDIT:

Same hang, but on "Check Install"...

---

### Post by serosis on 2010-03-16
UPDATE:

Used a different method, external HDD using "LinuxLive USB Creator".

Now at least it gave me an error message, only after I pressed a key though. It seemed to hang at a blank screen up until the moment I hit a key.

Since I obviously can not get a screenshot and I am too lazy to write it down I give you... ye olde screenshot:

[[IMG]http://img705.imageshack.us/img705/4009/dscn1154f.th.jpg[/IMG]](http://img705.imageshack.us/i/dscn1154f.jpg/)

Yeah, yeah, a CRT monitor. Had to give up my old flatscreen due to it being a large flat P.O.S.

---

### Post by prodigy_ on 2010-03-16
> **serosis said:**
> ye olde screenshot
Looks like you've hit [this](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/406192).

And generally (assuming that your hardware is ok) it seems that something in the kernel doesn't work quite as expected. Maybe a buggy driver?

If you have an external HDD, I'd suggest the following: install Ubuntu on the external drive (using some other PC) and then try to boot your PC from it. At least you'll get logs, possibly telling you what exactly goes wrong.

---

### Post by serosis on 2010-03-16
> **prodigy_ said:**
> Looks like you've hit [this](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/406192).

And generally (assuming that your hardware is ok) it seems that something in the kernel doesn't work quite as expected. Maybe a buggy driver?

If you have an external HDD, I'd suggest the following: install Ubuntu on the external drive (using some other PC) and then try to boot your PC from it. At least you'll get logs, possibly telling you what exactly goes wrong.

I think i have my old LTS cds lying around, but now I find that even my once bootable Bactrack 4 dvd is not booting proper.
Something to do with "squash", "inodes" and whatnot.

Then again i did install it to an external drive like ubuntu and my pc has an issue with booting from external media.

I'll burn a new DVD and see how that goes.

EDIT:

*Phew*, Backtrack 4 still works

---

### Post by serosis on 2010-03-24
Just tested my old 6.06 LTS CDs and my PC just vomited that there was an error in xserver.

I'll try it again and post a ye olde photo...

UPDATE:

[[IMG]http://img59.imageshack.us/img59/6159/dscn1163e.th.jpg[/IMG]](http://img59.imageshack.us/i/dscn1163e.jpg/) [[IMG]http://img340.imageshack.us/img340/2770/dscn1180d.th.jpg[/IMG]](http://img340.imageshack.us/i/dscn1180d.jpg/) [[IMG]http://img59.imageshack.us/img59/8271/dscn1182y.th.jpg[/IMG]](http://img59.imageshack.us/i/dscn1182y.jpg/)

What is awesome though is that I'm posting this within Ubuntu 8.04 :P

I don't know under what set of circumstances that allows 8.04 to work but not 9.10 and 6.06.

I'm gonna go ahead and install 8.04 onto my system, you guys can tell me if I can upgrade without botching it. ;)

---

### Post by serosis on 2010-03-24
OK, did the incremental upgrade all the way to 9.10 and bam, doesn't work.

All the upgrades worked up to 9.04 and as soon as it hit 9.10 on the restart, just gives me a black screen with no disc activity.

Tried going through the recovery and that booted, but of course no use to me being without a desktop.

So new question, can I downgrade to 9.04 through the recovery console?

EDIT:

I'm gonna see if the Beta works first before anything, be back with results later.

UPDATE:

Good news, the beta works flawlessly.
The only problem I have is that VLC won't play movies off my external drive (formatted in HFS+ for the XBOX 360).
But I got somebody to tell me that it's a bug in the HFS driver in the linux kernel. So yeah.

---

