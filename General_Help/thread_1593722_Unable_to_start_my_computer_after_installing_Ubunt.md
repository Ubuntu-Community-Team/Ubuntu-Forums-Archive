---
title: "Unable to start my computer after installing Ubuntu."
date: 2010-10-11
forum: General Help
---

### Post by MysteryPig on 2010-10-11
I have the Ubuntu 10.04 LTS (32 bit) CD that I requested from Ubuntu. I have two desktop computers, and after trying Ubuntu out for a month or so on my newer computer (which also has Windows XP on it), I decided to try and put it onto my older computer. Unfortunately, now whenever I start up my older computer, it runs through an Intel Pentium screen (which tells me to hit F2 if I wish to run setup, and F12 to boot from the network). After this screen, the computer beeps, and I get the message: 
error: No Such Device: 4b5b3e5c-77b3-4c56-8fa0-b6ld2db22461
grub rescue> (I can type here). 

I am unsure of what to do, because currently, I wish to rid the older computer of Ubuntu,  while keeping Windows XP, and do not know how to. 

I am not very experienced with Ubuntu, and have already tried a lot of the other threads solutions, but they either did not work in my situation, or I did not understand how to do them.

Thank you very much for your time, and I would appreciate any ones help.

---

### Post by cdgugler on 2010-10-11
Try this thread:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You will have to boot from a cd.

---

### Post by MysteryPig on 2010-10-11
Thank you for your help cdgugler.

I tried the thread you gave me, however when putting sudo fdisk -l into the terminal, only sda1 showed up and it was ntfs (I know this to be windows).

I am utterly confused.

---

### Post by wilee-nilee on 2010-10-11
Boot the Ubuntu live cd go to gparted in menu-system-admin and take a screenshot and post it.

---

### Post by MysteryPig on 2010-10-11
OK, here is the link to the screenshot:    [http://i53.tinypic.com/10d8w3m.png](http://i53.tinypic.com/10d8w3m.png)

---

### Post by wilee-nilee on 2010-10-11
You just need to reload the MS bootloader to the mbr. This can be done with any XP install cd, here us one if you don't have one. Here is a link describing the process.

[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

This will reload the XP bootloader then you just go to the Ubuntu folder and click on it's un-installer.

---

### Post by MysteryPig on 2010-10-12
OK, so I have downloaded both files, and unzipped "Universal Customizer" on my flash drive. Now I simply move "XP Home with drivers" onto the flash drive next to Universal Customizer" and then I have the equivalent to a cd to install Windows XP?

---

### Post by MysteryPig on 2010-10-12
Forget what I just said. 


On the window: [http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html), one of the final steps is to "Run Universal_Customizer.exe". However, when I try to run it with wine, i get the message: The file '/media/usb0/DELETELATER/Customizer/Universal_Customizer.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."


What am I doing wrong?

---

### Post by MysteryPig on 2010-10-13
So confused. :S

---

### Post by gordintoronto on 2010-10-13
Do you have a U3 USB flash drive, as is required for the instructions? U3 is very unusual, I have many flash drives, but I have never seen a U3 drive, just read about them. With a U3 drive, you would not run universal_customizer from Ubuntu, you would run it from Windows, booted from the flash drive.

Do you have a Windows install disc?

---

### Post by MysteryPig on 2010-10-14
I'm not sure if I have a "U3" flash drive or not...   However I do not own a Windows installation CD.

---

### Post by mastablasta on 2010-10-14
> **MysteryPig said:**
> However I do not own a Windows installation CD.
 
 
you should be able to recover it easilly with windows CD:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)
 
but since oyu dont' have a CD
 
do you maybe have floppy drive?:
[http://www.ehow.com/how_4910631_download-windows-xp-recovery-disk.html](http://www.ehow.com/how_4910631_download-windows-xp-recovery-disk.html)
 
basically you would use floppy as MBR to get in and then do the fixmbr command.
only device in this case would have to be specified to be your c:\ drive
 
one thing though...
 
you said you can't run Ubuntu yet liveCD runs just fine. how can that be? if live CD runs fine then so should the install. maybe it needs additional graphics drivers installed but it should work fine.

---

### Post by MysteryPig on 2010-10-14
mastablasta: first of all, thank you for the help.

However, I do not have internet access on my older computer, and my newer computer does not have a floppy disk drive.

---

### Post by mastablasta on 2010-10-15
Here is on creating USB disk:
[http://www.buzzle.com/articles/install-windows-xp-from-usb.html](http://www.buzzle.com/articles/install-windows-xp-from-usb.html)
 
also i think you could stick the files ment for diskette on USB drive instead. as long as the drive is bootable.
 
in addition you should be able to get a recover CD from Microsoft.

---

### Post by MysteryPig on 2010-10-15
Mastablasta, to get WinToFlash, I need the windows cd in the first place which I do not have.

Where can I get a Windows Recovery CD?

---

### Post by Solved on 2010-10-16
I have spoken with a friend, and he says that he can lend me his Windows Installation CD.
What are the steps to fixing my problem **with **the installation CD?

---

### Post by MysteryPig on 2010-10-20
Oh sorry, I created 2 accounts due to a mistake, and Solved = MysteryPig.


Turns out I **can't** get the recovery CD, so now I do not know what to do...

---

### Post by earthmeLon on 2010-10-21
Since the installation, did you modify your HDD configuration?  When Ubuntu installs, it gets the ID of the harddrive and uses that as reference for mounting.  If you remove/change your harddrives, or even modify the partition table, it is possible that this ID has changed.

There are a lot of links in this post, and I have not read them all, but re-installing Ubuntu sounds like a good option.

If you use the CD you installed Ubuntu with, you can boot into the Live CD version, which will give you access to your machine.  You could then mount the drive and check it's ID vs the settings in the drive's /etc/fstab

---

