---
title: "Keyboard layout indicator problem when using FreeNX server"
date: 2009-12-01
forum: General Help
---

### Post by lz1dsb on 2009-12-01
I decided to start a new thread about this problem, I encountered recently. Basically what I'm using is Ubuntu 9.04 Jaunty Jackapole running on a VMWare virtual machine (I don't know if this is relevant, but I have the edubuntu-desktop installed). I'm accessing the machine exclusively from remote. I was using x11vnc, but a colleague of mine told me about this freenx server and I decided to give it a try. So I've installed it, using all the instructions from here: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) (it's quite nice manual though, so I congratulate the authors). Now the freenx server is up and running and it's actually quite fast compared to VNC, but with two very nasty problems:
1. I encountered the problem described in this thread: [http://ubuntuforums.org/showthread.php?t=1337617&highlight=freenx](http://ubuntuforums.org/showthread.php?t=1337617&highlight=freenx) . I was able to apply the workaround (and it works), but it seems that after deactivating the keyboard plugin, I'm no longer able to switch between keyboard layouts. Only the default one: USA is active.
2. When I try to add a keyboard layout to the panel I get the following error:
"The panel encountered a problem while loading "OAFIID:GNOME_KeyboardApplet".
Do you want to delete the applet from your configuration?"
I get this error only the first time I try to add the indicator to the pannel. If I try once again, than the error is changing to:
""Keyboard Indicator" has quit unexpectedly
If you reload a panel object, it will automatically be added back to the panel."
So even if I select reload, the problem is still persistent. Interestingly, I'm able to add the keyboard layout indicator when I'm running VNC! So there seems to be a correlation with the freenx server. I'm using the latest version of freenx, from the link mentioned in [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX). Does anybody encountered such problem? Do you think I should post a bug in Launchpad?

---

### Post by lz1dsb on 2010-03-16
Just to add this. A colleague of mine tested this on Ubuntu Karmic and the keyboard layout problem was gone. So I guess this only affects Jaunty.

Cheers,
Boyan

---

### Post by sirpy on 2011-04-15
i've found this to work on ubuntu 9.04
setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,il

this sets the keyboard layout to us,il (us,israel) and the alt-shift to toggle. and it works!

---

### Post by lz1dsb on 2011-04-18
That's quite interesting. I'll check it out. Thank you so much for letting me know.


Cheers,
Boyan

---

### Post by lz1dsb on 2011-04-21
> **sirpy said:**
> i've found this to work on ubuntu 9.04
setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,il

this sets the keyboard layout to us,il (us,israel) and the alt-shift to toggle. and it works!
Thank you so much for this. I've been looking for a solution for so long and it really works perfectly. And it's just one command line ;( Thanks once again. 


Cheers,
Boyan

---

