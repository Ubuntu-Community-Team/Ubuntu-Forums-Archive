---
title: "Screen problem since update..."
date: 2010-07-14
forum: General Help
---

### Post by meburke on 2010-07-14
OK, here's the situation: For weeks now I've been running Lucid, Compiz enabled, and everything has been just fine except the screen saver. (I replaced the Gnome screensaver with xscreensaver, and it works fine, now, but it used to freeze after a couple of hours of random picture slideshow.)

Yesterday I got a notification about some updates available and I simply installed them all. When I turned on my system today, the video started acting up going into the Xscreen login page. I can hear the sound it makes when the screen shows up, and I can here the sound it makes when I log in blindly, but the video is simply a bunch of distorted white stuff at the top of the screen. I can Ctl-Alt-F1 to a terminal screen, and ps reveals that all my apps are running. If I then Alt-F7 to my X-Window session I get a blank screen. If I then try to go back to the terminal session it says "Input not supported".

lspci reveals: 00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

Xorg.conf only says:
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"		"uxa"
	Option		"EXAOptimizeMigration"	"true"
	Option		"MigrationHeuristic"	"greedy"
	Option		"Tiling"		"true"

apt-get install xserver-org-video-intel-2.4 or apt-get install xserver-org-video-intel simply tell me that they can't be found.

I've been trying to get the dpkg for xserver.org, but can't seem to find it.

I don't know enough about XWindows anymore to figure out where I need to go to reconfigure the "Configured Video Device", I don't know exactly what I would put in the xorg.conf using the old format (which still seems to work), and I don't know how to revert to the old device configuration.

I would like answers to all of these problems if someone can help, and I would appreciate any other suggestions you may have. If someone could point me to an up-to-date tutorial on handling the new X configuration, I would be very grateful.

Thank you in advance,

Mike

---

