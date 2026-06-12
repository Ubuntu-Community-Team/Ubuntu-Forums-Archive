---
title: "Failed Boot after Purple Ubuntu Screen"
date: 2012-07-18
forum: General Help
---

### Post by excetara2 on 2012-07-18
To describe what happened and what I've tried before the failed boot is this:
Compiz failed and I couldn't get it to relauch so I rebooted the system. Ever since, after the Ubuntu login screen (with 5 round circles in the middle. It just goes to the next screen which is black with various tasks displaying [OK] at the end and freezes. I've switched over to a terminal session and removed fglrx and reinstalled xorg-default drivers. This didn't help because I had a suspicion it was an issue with X. Not sure where else to go but a reinstall. Any one have any ideas to try or to get further where the boot is failing.

Of note, when I reinstalled to the open source drivers, I got a screen saying hardware not detected properly and I hit ok to continue for one session. Then froze at the same screen again so appeared not to be to open source or proprietary drivers.

Not sure where to go or how to further debug. Where is the log kept for the boot sequence (under /var/log/?? I'd guess but I guess any help would be great.

---

### Post by oldfred on 2012-07-19
Log files can be viewed with Log File viewer. They are in /var/log and some folders inside that for different appps. I usually look at dmesg first as that is the log of the boot process you can see on screen without quiet splash on the grub menu line.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

#To see video:
sudo lshw | grep -A 11 display
#Resolution:
xwininfo -root

#If able to boot to recovery mode & netroot
#list of recommended drivers:
jockey-text -l
#Install a driver:
sudo jockey-text -e <driver>

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

---

### Post by excetara2 on 2012-07-19
I don't have any problems with grub. Trying everything I could tell would be relevant on the video issues page didn't help. At least the kernal is booting but just problems launching graphical interfaces.

---

### Post by oldfred on 2012-07-19
Have you tried the nomodeset? Sometimes it is even other boot parameters that cause it to stop.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by excetara2 on 2012-07-19
Think it was something related to compiz conflicting. Ended up getting it to work by deleting all compiz traces in the home folder. Then just reloaded them with my exported settings.

---

