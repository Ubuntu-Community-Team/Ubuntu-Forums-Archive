---
title: "Ubuntu 11.04 Problems."
date: 2011-04-28
forum: General Help
---

### Post by Zach G on 2011-04-28
So, I recently installed, or.. ermm.. Tried to install Ubuntu 11.04, I did it with a CD.
This is about my 4th time around with Ubuntu, so I'm not completely new to it. 
But, I used to have Windows 7 on here, and I decided I wanted to go with Ubuntu, so I downloaded and burned the CD, and did all the stuff you need to do to install Ubuntu. I got far into the installation, and then the installer crashed saying something about an Input/Output error, and it could be the CD being dirty or damaged.

Now, I'm stuck with a broken operating system because I chose to replace my Windows 7 partion with Ubuntu, and there's no terminal! Everything else seems to be here, it's just really buggy, and I can't get much of anything installed.
Did I mention there's no &^&%%$&* terminal!? HELLLLLPPPPP!!:confused:

---

### Post by Zach G on 2011-04-28
Can somebody please tell me what the hell is wrong?

---

### Post by hwttdz on 2011-04-28
You can try "alt+f2" and then running "gnome-terminal".  If that doesn't work you can do "ctrl+alt+f2" and that will drop you to _the_ terminal (which is pretty much the guts of the linux os, if you have anything you have this terminal).  And from there you can do apt-get update, and apt-get upgrade, and that should sort of finish up the install if there are any issues.

---

### Post by RavanH on 2011-04-28
As it is completely unclear what did and what did not end up on your HDD, it will be useless to try and fix it 'from within' (read: from terminal) even if it would be possible to do a login.

There is only ONE thing you can do here: re-install... Try the same CD after making sure there are NO fingerprints/smudges on the surface and hit any key right after the system starts up from the CD when you see two little icons of a keyboard and a man at the bottom of your screen. You will get to see the boot menu and there is an option to "Check CD for defects" or whatever it's called. 

If that does not result in any defects being detected, try to install again from the same CD. But if you run into the same problem again, you will have to get another copy preferably on a better quality CD. 

If you do not have access to anyone with an internet connection and a good burner (producing a good burn on good quality CD's) there is always the option to order an installation CD or USB stick from [http://shop.canonical.com/](http://shop.canonical.com/) ... Even though 11.04 is available yet, you can get your machine up and running with 10.10. Note that for a USB stick your computer must be able to boot from one and CD's come in packs and cannot be bought single so you will have to order either a pack of 3 different distro's or 5 of the same distro.

Good luck!

---

### Post by KegHead on 2011-04-28
Hi!

I'd try a reinstall with a USB stick.

[COLOR="Red"]Backup if you can.[/COLOR]

KegHead

---

### Post by Zach G on 2011-04-28
I just got this when I FINALLY got into terminal and tried to update/upgrade..


E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by Zach G on 2011-04-28
Well, I got terminal working, and upgraded/updated worked, I just had to put sudo behind the command.

---

### Post by DirkJDiggler on 2011-04-28
Hello, I'm new this forum.
 
I installed 10:10 on an Acer Aspire One. WL was not working so I thought I'd install 11:04 from the Update Manager.
 
The install is complete. But all I see when logged in is the background and a mouse pointer. I managed to get toa terminal window and tried the sudo apt-get-update and I get command not found.
 
Help please.

---

### Post by VanR on 2011-04-28
Try sudo apt-get update. No dash between get and update.

---

### Post by DirkJDiggler on 2011-04-28
Legend. The power of a "-".
 
Thank you. I'm now rebooting. Fingers crossed I get a usable interface.

---

### Post by DirkJDiggler on 2011-04-28
Damn. Rebooted and still stuck on a background with nothing but a mouse pointer. My daught er is going to kill me. I may well have stuffed her Netbook.

---

### Post by Aaddron on 2011-04-28
> **DirkJDiggler said:**
> Damn. Rebooted and still stuck on a background with nothing but a mouse pointer. My daught er is going to kill me. I may well have stuffed her Netbook.

Try this, on the login screen click the user name then at the bottom of the screen there should be 3 boxes, one says "Ubuntu" click the arrow button next to it and select "Ubuntu Classic No Effects" then try to login.

---

### Post by DirkJDiggler on 2011-04-28
From GRUB I am booted straight to the Background. i don't get a login screen.
 
Any other thoughts?

---

### Post by Aaddron on 2011-04-28
Not really, sorry, I'd suggest making a live CD or USB to see if 11.04 works with the hardware, if that works fine then it means something went wrong with the upgrade in which case someone more knowledgeable might be able to help you fix it or you could just install over it.

---

### Post by DirkJDiggler on 2011-04-28
Interesting thread here. Seems very relevant. Appears to be an issue with 2D/3D Unity. 
[http://ubuntuforums.org/showthread.php?t=1721167](http://ubuntuforums.org/showthread.php?t=1721167)

---

