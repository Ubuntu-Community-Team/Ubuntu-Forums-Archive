---
title: "Screensaver? (inactivity &gt; gray screen with an X)"
date: 2009-11-06
forum: General Help
---

### Post by gstuart on 2009-11-06
Hello - I upgraded from Ubuntu 9.04 to 9.10 a couple of days ago.  This evening I noticed that my computer - after some minutes of inactivity, goes to a gray screen, with a big X (the X.org logo?).

It's damned annoying; I never want the screen non-visible.  I checked the obvious: Power Management and Screensaver (System > Preferences), and gconf (apps > gnome-screensaver), and everything is set to not have this happen.

Can anyone explain what is going on?

Thanks, Victoria  :-)

---

### Post by gstuart on 2009-11-06
It was the simplified X.org logo (just the "broken X," without the encircling colored loop), popping up on a blank gray screen after 10 minutes of inactivity (I sat, watched and waited!  :-p

Here is the problem, described:

[http://www.shallowsky.com/linux/x-screen-blanking.html](http://www.shallowsky.com/linux/x-screen-blanking.html)

and 

[http://ubuntuforums.org/archive/index.php/t-584502.html](http://ubuntuforums.org/archive/index.php/t-584502.html)

I remember having this problem in 2007: then, my screen was fading to black, after 10 minutes, independent of Power Management or Screensaver settings.  I had to edit my /etc/X11/xorg.conf file, as described in the above links, 

...
Section "ServerFlags"
	Option "Xinerama" "0"
	Option "DontZap"  "True"
	Option "BlankTime" "0" #This blanks screen
	Option "StandbyTime" "0" #This is DPMS
	Option "SuspendTime" "0" #DPMS
	Option "OffTime" "0" #DPMS
EndSection

sometimes (various threads) there are spaces, i.e.

	Option "Blank Time" "0"
	Option "Standby Time" "0"
	Option "Suspend Time" "0"
	Option "Off Time" "0"

but I don't know if it males a difference, or if you have to restart X to have the settings take hold.  But, I'm pretty certain that this is what's going on.

Victoria  :-)

---

### Post by gstuart on 2009-11-06
Update: I did have to reboot - problem solved!  :-)

---

