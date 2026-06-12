---
title: "unetbootin problems after installing Win7"
date: 2010-01-17
forum: General Help
---

### Post by jrowland on 2010-01-17
So I've been running Ubuntu in a VM environment for a while, seeing if I like it. I think it's something I'd like to have as the primary OS on my netbook, so I downloaded the latest Netbook Remix version (9.10).  Problem is, I can't get the thing to boot from my USB stick. 
 
Before we get into any lessons on how to set up a USB stick to be bootable, and how to adjust the BIOS's boot priority... let me say that I've used this exact stick and this exact laptop in the past just fine. When my netbook came home from the store with WinXP on it, I created a Live USB using unetbootin v3.56 and made the stick bootable with a gparted-live ISO. I used this to boot from the stick and partition my drive in half so that I could load the Win7 RC onto the other partition. Everything worked great then. I blew away those partitions and went back to a single partition when I loaded up my full Win7 OS a few weeks ago. 
 
I'm wondering if it's possible that Win7 does something special with the bootloader to prevent this stick from being recognized? I know that sounds kinda far fetched, but I have a vague sense of having read this somewhere, but I can't find anything along those lines now. 
 
Just to be sure, I went into the BIOS and took out both the CD and the HDD from the boot sequence, so the only thing in there was the "removable device". However, when booting from the stick in this configuration, I got a "please insert an operating system" type message. 
 
When I started this process, the stick was still in "LiveUSB" mode with the gparted OS - however, I didn't test it in Win7 to see if it would have booted from it. I just assumed that it would have since the last time I used this USB stick, it was to boot into gparted-live. 
 
Here's what I've tried so far: 
+ formatted the stick via the Windows Explorer right-click-format routine (quick format, FAT32). 
+ re-ran unetbootin with the Remix.ISO (no joy) 
+ re-formatted, downloaded the latest unetbootin version (v3.77), and tried the Remix.ISO again (still nothing) 
+ re-formatted, tried using the unetbootin "on board installer" for Ubuntu 9.10 (where it goes out and fetches the image instead of using a .ISO).  Still no joy, even though that would have been the desktop version instead of the netbook remix.  Just testing.
+ re-formatted, tried going back to the gparted-live stick with the same process that I used originally (except that it was from within XP, now this was in W7). No dice there, either.
 
Any ideas on where I might be going wrong? Is my idea on the Win7-bootloader-blocking-the-stick idea valid at all? My USB stick /does/ go blinky-blinky a few times when the computer is booting.

---

### Post by jrowland on 2010-01-17
I just ran a test to prove that it wasn't the USB stick causing problems... I just booted my wife's desktop from it, and it booted into the LiveUSB environment just fine.  The desktop is a new HP system that came loaded with Win7 Home 64bit OEM.  So, it's not purely a Windows 7 thing.

I also tested my laptop's boot priority by using a physical CD, and it booted from CD just fine.

a few more details on the netbook... it is an Asus EeePC 1000HE model with 1G ram.  I upgraded from the OEM WinXP to Win7 Home Premium off of a "Family Pack" that we bought to upgrade the wife's and kids' laptops.  Figured since we still had 1 license left, I would upgrade mine as well.  

I'd still like to dual-boot this with Ubuntu as the primary OS, but I need to get the stick working, so if anyone has any great ideas, I'm all ears.  I'd just create a LiveCD, but I'll be damned if I can find any blank CDs just laying around... that's almost as archaic as a floppy these days.  Since I don't do a lot of playing, I don't really have a need for blank CDs. :/

---

