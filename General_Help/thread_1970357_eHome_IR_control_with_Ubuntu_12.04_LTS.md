---
title: "eHome IR control with Ubuntu 12.04 LTS"
date: 2012-05-01
forum: General Help
---

### Post by Voyager576 on 2012-05-01
I have installed Ubuntu 12.04 LTS on my Lenovo T61 laptop, and it works great. From slick installation process through intuitively learning my way around the desktop, to using the applications installed, it has been a painless process. :)
 
As the T61 has a docking station, the icing on the cake will be to use it as a media streamer, either undocked on lap, or docked with external flatscreen. The latter will be more convenient with a remote control, so I'd like to use a spare MS eHome IR receiver and remote control that I already own. Yes, I can buy another Boxee Box like I already own for the living room, but that's too easy and costs money!
 
[This]("http://markbrewster.wordpress.com/2010/01/15/enabling-lirc-for-microsoft-mce-remote-control-in-ubuntu-9-10/") thread looked promising as to what to do, but the installation process fails with lots of "wicked errors".
 
I'm happy to spend time learning rather than blindly following instructions, but would appreciate some pointers, please, regarding how to get the IR receiver to work with Ubuntu 12.04.
 
Many thanks,
V576

---

### Post by Voyager576 on 2012-05-01
The problem appears to be partially solved simply by moving the USB connection to another port.  XBMC now at least partially responds to the remote control (some commands work, but most do not).

I'll now do some further research and revert if I need to. :p

---

### Post by Voyager576 on 2012-05-01
A courtesy post to close the thread;  I have been able to find all that I needed and my (genuine) MS MCE remote control now controls XBMC perfectly.

The world certainly has plenty of ills, but it is also an amazing place.

Very happy.

:grin:

---

### Post by robertfullarton on 2012-05-19
Hi, I'm also using a MCE eHome IR 0471:0815, it was working ok when I first upgraded to 12.04 then stopped working altogether when I did an update recently. I have 3 systems here running mythtv and all three are the same , remote stopped working.

I found a post in a XBMC forum and it mentioned having the following in the /etc/X11/xorg.conf file.

Section "InputClass"
Identifier "Remote"
MatchProduct "Media Center Ed. eHome Infrared Remote Transceiver"
Option "Ignore" "True"
EndSection


This stops X from taking over the MCE remote. Now my remote works as before..:p

---

