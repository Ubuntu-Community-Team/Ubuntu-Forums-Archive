---
title: "Error 18 on Post ( And one other issue)"
date: 2009-08-27
forum: General Help
---

### Post by jkb609gi8 on 2009-08-27
First Issue
 

 The other day when Ubuntu was running fine, I did something stupid.
 I had to leave my shack in a hurry so I force shutdown my Aspire 5040
 while using the video player.
 

 The next morning when I tried to boot, I only got a short distance until  
 the following last few lines:  
 “ Grub loading stag1.5.
 Grub loading please wait...
 Error 18 “
 

 This is what I tried:
 

 I put the live Ubuntu 9.4 boot DVD disk back into the machine and found it work up until the piont  were I tried to Ubuntu from the disc.  
 

 I found that from the Disc the Error 18
 

 So I did memory test with memtest86 v2.11
 Chipset: AMD K8 (ECC  disabled)
 Setting:  RAM 163 Mhz
 

 Here are the results:
 ( Please note that the test just kept going over and over itself in a repetitive manner. )
   **************
 Walltime     1:17:00
 Cached        894m
 RsvdMem   130m
 MemMap     e820-std
 Cache           on
 ECC             off
 Test              std
 Pass              7
 Errors           1
 ECC Errors   0
  ****************
 Tst                        6
 Pass                      1
 Failing Address     0002fed3da8-766.1MB
 Good                     7fffffff
 Bad                        7fffdfff
 Err-Bits                  00002000
 Count                     1
 Chan
   ****************
 From the Ubuntu 9.4 boot disc I also did a “ Check disc for defects” test.
 The screen just show data process with white test and a black background like you would find on the screen while using a command line shell.
 

 The computer just kept processing data in a repetitive manner.
 The following strings kept reappearing along with other strings.
 

   ****************
 [ 289.459 ] (Note this number is on the right and keeps changing as things process in repetitive manner.
   ****************
 ata1.00 status: {DRDY ERR}
 ata1.00 error: {UNC}
 ata1.00 exception Emask 0x0 Sact
 ata1.00 BMDMA Stat 0x24
 ata.100 Cmd C8/00:08:40:00:00:00:00:00:00/eo Emask OX9 (media
 

  Anyways, your Idea's and suggests welcome.
 

 

  ************************************************************************
 Second Issue  
 

 ((( NOTE: Perhaps this note will show you that I do not know a hell of a lot about computers. :confused: My BIOS may have been bugger by the Microsoft XP, this was on the system before, or by a virus when the system was run on Windows XP. I had the XP that came with the machine crash, and I could not recover it, so ended up loads loading a bootlegged version of XP, so I could get the DVD driver to work, then I wiped out the XP with Utunbu 9.4.  Perhaps windows managed to “call home” and they somehow bugger my BIOS. I Love kicking the Microsoft Dog, although I am probably wrong. :guitar:  )))
 

 When I discovered the Error 18 boot problem with Ubuntu, I first went into my BIOS, and the setup utility. On this Acer machine it is a PhoenixBIOS. I found many of the settings would not allow change.
 I could only access about half of the settings that I once could.
 In security I could access the User Password, however not the Supervisers Password.
 I cannot Select Items with keyboard arrows in Secuirity Sub-Menu.
 

 I could not “Set Defaults” when I was suppose to upon entering F9.
 

 When I go to the Boot, Sub-Menu I cannot Select the CD-ROM/DVD Drive.
 The Item Specific Help states: “ All items on this menu cannot be modified in user mode.
 If any items require changes, please consult your system Supervisor.”
 I am not promte anywere in the Setup Utility for the Supervisors Password.
 I cannot Select the Supervisors Password in the Security Sub-Menu.
 I can only access  the User Password.


 Anyways, your Idea's and suggests welcome.

---

### Post by bchurchill on 2009-08-27
It sounds like your GRUB may have gotten corrupupted (hey, I think I've answered this type of post three times today already).

Go into the live cd, and see if /boot/grub exists on your hard drive.  If it does, look for the stage1, various stage1_5 and stage2 files.  If they aren't there you'll need to reinstall grub:

[https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows)

Also try booting into recovery mode and running fsck (or do it from the livecd).  Other things may be corrupted as well.

BTW are you using ext3 or somthing else?

-----------------------

I don't know about the BIOS.  Sounds like someone put a password on it without your permission.  I believe removing that will take some work.  I can't really help you there....

---

### Post by jkb609gi8 on 2009-08-28
Well it maybe a few days before I will have any more time to deal with this problem. For one thing I have to figure out how to open the terminal from the live disc. (This Utuntu disc I had got from Canonical)

---

