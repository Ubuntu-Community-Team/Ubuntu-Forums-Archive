---
title: "lucid no login dialog box"
date: 2011-07-22
forum: General Help
---

### Post by pi3guy on 2011-07-22
**Edit** I was able to get ubuntu working by uninstalling zlib, gmp-4.3.2, paramiko, and pycrypto

Hello everyone,

I recently upgraded from 9.04x64 to 10.04x64 lts and had just got everything running smoothly. (ati drivers were working perfectly). I was trying to install some python modules paramiko and zlib when I wanted to restart or logout, but when I reach the purple login screen, there is nothing to interact with. I hear the bongo sound and can move my mouse cursor but nothing else appears. 

I can login with ctr alt f1-f6

Some things I've tried without success(I did some research before posting a new thread)

waiting 10+ minutes; nothing changed

sudo gdm -restart; error -failed to acquire org.gnome.DisplayManager; there was another error line after this

booting into recovery mode, running in low graphics mode; same result

sudo dpkg --configure -a

sudo apt-get update; with ethernet plugged in

renamed xorg.conf in hopes ubuntu would create a new one

checked kernel uname -a, correct 2.6.32


can anyone give me some tips to recover ubuntu? I am hesitant to reinstall as I have a dualboot with windows that I don't want to mess up.

thanks for your time

---

### Post by pi3guy on 2011-07-23
I have made some progress. By booting kernel 2.6.32 recovery mode and repairing broken packages, I am able to get to a nearly normal gui desktop. 

  However, the right side of my top panel is blank, ie missing clock, shutdown, etc and I have corresponding error messages such as: 
The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet". Do you want to delete the applet from your configuration?
My bottom panel is also empty, missing trash and buttons for open programs.

When I try to "Add to Panel", all the same error messages pop up again.

Finally, repairing packages does nothing for my regular 2.6.32 kernel and it is still missing the login box.

hope someone can help me out
thanks

---

