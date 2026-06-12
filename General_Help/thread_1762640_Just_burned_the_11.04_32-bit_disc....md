---
title: "Just burned the 11.04 32-bit disc..."
date: 2011-05-19
forum: General Help
---

### Post by David2009 on 2011-05-19
...and, I wanted to boot with the disc to see the new look.  I turned the computer off, placed the disc into the DVD player (Toshiba Satellite laptop), and turned the computer on.

I saw a couple of icons at the bottom of the screen.  I really could not say what these were.  After a minute or so the screen went blank.  Enter didn't do anything.  ESC didn't do anything.

I turned off the unit and rebooted.  This time, when I saw the icons I hit the enter key.  I saw the screen with all of the languages to select.  

To ensure that I didn't accidentally install the software, I hit ESC.  This returned me to the page with the option to give Ubuntu a try without installing.

I hit that option, and nothing happened.

What's up?

Thank you.

---

### Post by oldfred on 2011-05-19
I have not tried Natty on my Toshiba yet, but for the last few versions I have had to add nomodeset on my desktop.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by philinux on 2011-05-19
> **David2009 said:**
> ...and, I wanted to boot with the disc to see the new look.  I turned the computer off, placed the disc into the DVD player (Toshiba Satellite laptop), and turned the computer on.

I saw a couple of icons at the bottom of the screen.  I really could not say what these were.  After a minute or so the screen went blank.  Enter didn't do anything.  ESC didn't do anything.

I turned off the unit and rebooted.  This time, when I saw the icons I hit the enter key.  I saw the screen with all of the languages to select.  

To ensure that I didn't accidentally install the software, I hit ESC.  This returned me to the page with the option to give Ubuntu a try without installing.

I hit that option, and nothing happened.

What's up?

Thank you.

Choose the option "Check Disk for Defects". And then report back with result.

What are your pc specs?

---

### Post by compmodder26 on 2011-05-19
Sounds like a bad burn.  Do a checksum on the ISO you downloaded.  If it matches the checksum on the Ubuntu download site then you know your ISO is ok.  Try burning the ISO again, perhaps at a lower speed.  Then when you boot the CD again, there should be an option to check the CD for errors.  Try that to verify that the CD is ok.

---

### Post by jrsutton on 2011-05-19
I've also found that downloading the .iso with a web browswer from Ubuntu won't always download correctly, but you can't tell the difference because it just tells you that it "completes". If you use the .torrent files to download the .iso you will not have this problem.

---

### Post by David2009 on 2011-05-23
Thanks to all you replied.  I was not able to find the instructions for viewing the CHECKSUM.  I remember doing this on a previous version, but did not find it this time.  I did another download, and burned another disk at 16x.  Same results as before.  I see those icons at the opening screen (looks like a computer = person).  Next, immediately I see the option for selecting a language.  Since, I don't want to accidentally install the program, I hit the ESC, and see the page with "try before install", "check disk for errors", "run from hard drive", etc.  On the newly burned CD, I tried the "try before install" option.  The computer hangs.  I end up rebooting.  I try "check disk for errors".  The computer hangs.  I end up rebooting.  
 
Here are my computer specs:  
 
Toshiba Satellite A305-S6861 / Windows 7 Home Premium / 32-bit / Service Pack 1 / Intel Core 2 Duo T5750 @ 2 Ghz

Have a great day.

David

---

### Post by Quackers on 2011-05-23
Here's a link for the md5sum info
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And here's a link for using boot options (you may need one or more with that setup - possibly acpi=off)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by David2009 on 2011-05-28
Thank you for the download site for md5sum.  The hash info is the same for the ISO.  
 
I guess the next idea is to go the torrent route.

---

### Post by David2009 on 2011-05-28
> **philinux said:**
> Choose the option "Check Disk for Defects". And then report back with result.

What are your pc specs?
I was not able to get the CHECK DISK option to run.  The screen froze.

---

