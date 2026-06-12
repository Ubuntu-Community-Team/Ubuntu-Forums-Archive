---
title: "Machine freezes when screen not attached (possible screen saver issue)"
date: 2010-03-17
forum: General Help
---

### Post by houldsworth1 on 2010-03-17
I have a PC running Ubuntu 9.10 and I need to remove the screen from it - it is only running a web server so I just need to access it remotely.
 
I managed to get to the point where I can start the machine without the screen attached by disabling the GUI (see [http://ubuntuforums.org/showthread.php?t=1412565&page=2](http://ubuntuforums.org/showthread.php?t=1412565&page=2)). I then access it using SSH.
 
The machine works fine for about 10 minutes and then completely freezes up to the point where even the keyboard caps lock key won't work. I then have to power down the machine to get it started again. The interesting thing is that this doesn't happen of the screen is attached.
 
So, my assumption is that the screen powersave mode is kicking in and, when the screen is not attached, it gets confused and hangs.
 
I created an xorg.conf file with some options that I hoped would stop this happening following this thread [http://ubuntuforums.org/showthread.php?t=1428387&highlight=monitor+turning+10+minutes](http://ubuntuforums.org/showthread.php?t=1428387&highlight=monitor+turning+10+minutes) but the problem is still occuring.
 
Anyone have any other ideas on how to stop this occuring?
 
Thanks!

---

### Post by houldsworth1 on 2010-03-26
Solved it.  Found this solution in another thread:

[COLOR="Red"]First, In /etc/default/grub, Change this line (sudoedit or whatever you like) :
Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
for
Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
then run
Code:
sudo update-grub
[/COLOR]
I have been running without the screen for a good hour now and now issues.

---

