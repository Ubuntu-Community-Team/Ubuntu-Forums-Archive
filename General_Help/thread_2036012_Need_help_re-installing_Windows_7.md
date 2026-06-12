---
title: "Need help re-installing Windows 7"
date: 2012-07-31
forum: General Help
---

### Post by ChrisWV on 2012-07-31
This might have been posted before, and if it has, I would appreciate someone directing me to the post
 
Anyway, I have an emachines latop that originally came with Windows 7.  After about a year I decided to go with Ubuntu totally and did so but not before creating my recovery disks.  The problem now is that I want to go back to Windows 7 but ubuntu will not read the disks.
 
I put the disks in a Windows 7 machine and there is recovery data on the disk so its good.  I set the bios to load DVD/CD Rom first and when I put in the recovery disk, it reads the disk but eventually loads Ubuntu.
 
What am I doing wrong?  I have racked my brain searching the net for a solution but I dont think I am finding the right help.  I am not so tech savy so can someone please help me out and tell me what I need to do?
 
Thanks

---

### Post by ahallubuntu on 2012-07-31
Either the Windows 7 recovery disc you made is not a "bootable recovery disc" (discs may contain data but cannot be used to install Windows 7 from scratch)...or you are not really booting the first disc.  If you installed Ubuntu I assume you know how to boot a CD on this computer...

You can burn your own clean Windows 7 install DVD by downloading it off the web and use the product key that matches the Windows 7 version on the sticker on the bottom of your laptop.  Download a Windows 7 ISO file from Softpedia (google around, easy to find).  The version should match your product key (so if you had Windows 7 Home Premium download that version).  32 or 64 bit should not matter, the same product key should work for either.  You will probably have to download drivers from the eMachines website to install after Windows 7 has downloaded.  Be sure to grab those FIRST while you still have Ubuntu - put them on a flash drive or something, at least the wireless card driver.

You'll have to activate Windows after the install.  If you can't activate it over the internet you may need to activate over the phone with MS.

---

### Post by oldfred on 2012-08-01
Recovery disks are not an install disk. They usually are just an image of hard drive as purchased. As such they usually just overwrite partition table and destroy everything you have on system, so backup before using.

Window installs and maybe your version of recovery have to see a primary NTFS partition with the boot flag. Since your system was originally a Windows 7, it proably had two Windows partitions and two vendor partitions. Windows uses a small 100MB boot/repair partition and the main install. Tne vendor uses a recovery partition or image (instead of shipping a set of DVDs to reinstall) and often a utilities partition.

---

### Post by ChrisWV on 2012-08-01
OK, I didnt know I couldnt use just the recovery disk.  Forgot that the product ID is on the bottom of the laptop (little hard to read but I got it).  I will try the download of Windows 7 install DVD.
 
Thanks guys

---

### Post by ChrisWV on 2012-08-01
OK so I created a Windows Install disk. When restarting the laptop, it stays on a black screen with a cursor blinking for about a minute and a half then boots into Ubuntu.
 
I also tried other CD's/DVD's to see if they would play and they don't.  This is the first time I've actually used the drive since going to Ubuntu.

---

### Post by drmrgd on 2012-08-01
It still sort of sounds like you don't have a bootable Windows install CD, and what's going on is the BIOS is trying to load an OS from the CD, can't see anything bootable, and moves on to the next item in the list, which will be your Ubuntu OS drive.  I'm guessing it's just moving on without throwing an error to tell you there's a problem with the CD.  

How did you make the Windows installation cd?  If you just downloaded an .iso or something and copied it to a CD, that won't be enough.  You'll actually need to use it and choose to make a bootable CD with the burning software you're using (Brasero?).

---

### Post by Moif_Murphy on 2012-08-01
If you want to wipe your current Ubuntu installation and start from fresh then I recommend downloading whatever version of Windows 7 your product key is valid for and installing from USB. 
 
I imagine your laptop has a sticker advising you of the version of Windows - be that Home Premium or Professional. You'll also need to know if your laptop is 64 or 32bit. Again, I'd imagine it's 64 bit. And finally you should boot into your BIOS and check to see if you can boot from USB. If you can then read on.
 
You can download the ISO's direct from Microsoft here:
 
[http://www.heidoc.net/joomla/technology-science/microsoft/14-windows-7-direct-download-links](http://www.heidoc.net/joomla/technology-science/microsoft/14-windows-7-direct-download-links)
 
I'm going to guess that it's 64bit Home Premium and so you'll need this link:
 
[http://msft.digitalrivercontent.net/win/X17-58997.iso](http://msft.digitalrivercontent.net/win/X17-58997.iso)
 
Then you'll need the USB / Tool. What this does is format your USB pen drive (make sure you have one which is 8GB or more in capacity) and copys the ISO contents over making it bootable. It's a free and available from Microsoft:
 
[http://emea.microsoftstore.com/UK/en-GB/Service-Centre/Windows-7-USB-DVD-Download-Tool](http://emea.microsoftstore.com/UK/en-GB/Service-Centre/Windows-7-USB-DVD-Download-Tool)
 
Once done, power off the laptop, set the BIOS to boot from the USB device, shut it down again, insert the USB drive power on and away you go.
 
Obviously you'll need another Windows machine to do all of this from but it works every time that I've used it.
 
:)

---

