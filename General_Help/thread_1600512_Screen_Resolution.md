---
title: "Screen Resolution"
date: 2010-10-19
forum: General Help
---

### Post by ali566 on 2010-10-19
I am using Duel monitor DELL AS502 & DELL 1905FP.
I am using DELL laptop workstation (Precision M 6300) and unable to get resolution more than 1280 x 800 on DELL AS502.
Can someone help me with this please?
 
Cheers

---

### Post by lotharmat on 2010-10-19
You're using a fighting monitor??? ;)

Have you got the 'same image in all monitors' checked? If you have you will only be able to have the resolution of the lowest one.

What you need to do is extend the primary onto the secondary and drag it to the same configuration as on your desk.

That should give you the ability to have different resolutions.
I'm currently using a Fujitsu Laptop at 1024x768 and a dell 19" at 1280x1024 with no problems.

Hope this helps,

PS - Duel = a fight; dual = two - Common mistake but one of my bugbears. - Apologies if my sarcastic opening caused offence

---

### Post by ali566 on 2010-10-19
Hi lotharmat,
Thanks for your reply. My mistake to spell duel wrong :) but I am kind of fighting with the screen resolution.
 
My issue is I having the maximum resolution of 1280 x 800 available for DELL AS502. 
How can I increase this?
 
The other monitor is fine and no problem in having different resolution on each monitor.
Cheers

---

### Post by koesjan on 2010-11-04
Hi ali566,

I'm not sure whether it can help you. I have an undetected monitor and I use this guide to help:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

In your case you can try:
$ cvt 1280 800

You will find a result like that, not exactly that one:
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline[COLOR=Black] _"1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync_[/COLOR]

Then copy the information after the word "Modeline" into the xrandr command: 
  $ xrandr --newmode [COLOR=Black] _"1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync_[/COLOR]

Test if your new resolution is working.

This will work just for the session, to add permanently I normally modify gdm profle:

Both KDM and GDM have startup scripts that are  executed when X is initiated.  For GDM, these are in /etc/gdm/ , while  for KDM this is done at /etc/kde4/kdm/Xsetup.  In either case, you can  paste in an xrandr command line string into one of these scripts.   For  GDM, try putting them right before
initctl -q emit login-session-start DISPLAY_MANAGER=gdm in /etc/gdm/Init/Default 
This  process requires root access and mucking around in system config files,  but will take effect earlier in the startup process than using  .xprofile, and will apply to all users including the login screen. 

I hope this can help you.

---

