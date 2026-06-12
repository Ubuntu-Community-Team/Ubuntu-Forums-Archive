---
title: "Problem with display"
date: 2011-03-12
forum: General Help
---

### Post by chkneater on 2011-03-12
My tower fell this morning while it was off but plugged in.  I had to recover the grub which I was succesful at but now I am stuck with the two lowest modes of resolution.  I have a Nvidia 5500 Geforce and it is still showing up along with the drivers.  I am going to reboot to that drive and reinstall the driver IF I can get a connection (Wifi probs? STILL??!) 

In the meantime if anyone else has any advice or ideas whilst I try reinstalling the driver I would deeply appreciate it.  I would take the time to scroll the forum but it is unbelievably hard to even use this thing right now.

---

### Post by chkneater on 2011-03-12
Ok, just in/reinstalled the Nvidia 173 driver and I still can't get resolution over 640.  I noticed something in the nvidia-settings it refers to the monitor as a CRT but it is an LCD.

Anyone have any ideas?

---

### Post by chkneater on 2011-03-14
Ok, so the fall made it lose some of the GRUB and the Xorg settings.  The xorg.conf was stuck with the backup settings for some reason.  So I copy/pasted a different xorg.conf from a different drive and then I was getting a horizontal sync issue.  Fixing the horizontal sync in xorg fixed it and now I have what was three days ago garbage, Thank God!  

It's ironic too that the tower fell because I was trying to change monitors to a ViewSonic someone gave me that was "broke".  I looked at it and a capacitor was blown so I fixed that and almost blew up the tower to have this huge monitor!

For anyone having issues with your monitor displaying "out of range horizontal sync" or something similar, especially after kernel changes or something, two hints: First, your system is still up, you just can't see it.  If you can get to a terminal either with muscle memory or keystrokes, do 'sudo dpkg-reconfigure -phigh xserver-xorg' and it should reset the xorg.conf file.  Option two, access with another installed version and change your /etc/X11/xorg.conf file with sudo gedit so that if you see a line that says "HorizontalSync", lower it in increments of 5, save, and boot.  Repeat process if your still getting the same message until you get in.

Another thing, if I'd been more careful an A) not let the damn thing fall and B) not had it plugged in at the time I probably wouldn't have had any problems.  I'm just surprised there was no data loss!?!

---

