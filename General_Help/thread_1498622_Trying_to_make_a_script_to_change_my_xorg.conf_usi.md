---
title: "Trying to make a script to change my xorg.conf using zenity"
date: 2010-06-01
forum: General Help
---

### Post by toxicfeet on 2010-06-01
Ok so I have a triple monitor setup and a TV hooked up to my computer. I have been working on a script to change the xorg.conf file to three different modes 

Single Monitor
Triple Monitor
Triple Monitor w/ TV

The main reason for this is I don't like my icons piling up on a monitor when I don't use it or new windows opening on a monitor that is off, ie my TV is at the far left.

I have been reading some basic bash scripting guides and I came up with this:

[q]#!/bin/sh

ans=$(zenity --width 400 --title "Pick a screenlayout mode" --text "Please pick an option" --list --radiolist --column "Option" --column "Mode" TRUE "Normal Three Screen Setup" FALSE "Normal Three Screen Setup With TV" FALSE "Single Monitor Setup");

echo $ans 

if [ $ans = "Normal Three Screen Setup" ] ; then 
	cp /etc/X11/xorg_3screen.conf.backup /etc/X11/xorg.conf
else
	echo "Working on it!"
fi



if [ $ans = "Normal Three Screen Setup With TV" ] ; then	
	cp /etc/X11/xorg_with_tv.conf.backup /etc/X11/xorg.conf
else
	echo "Working on it!"
fi



if [ $ans = "Single Monitor Setup" ] ; then
	cp /etc/X11/xorg_mainscreen.conf.backup /etc/X11/xorg.conf
else
	echo "Crap! its broken"
fi


zenity  --notification  --window-icon=update.png  --text "Your xorg.conf settings have changed, restart X11 server to see the effects."

exit
[/q]

[q]
------@----------:~$ sudo screenmode 
[sudo] password for tux: 
Xlib:  extension "RANDR" missing on display ":0.0".
Normal Three Screen Setup
[: 11: Normal: unexpected operator
Working on it!
[: 19: Normal: unexpected operator
Working on it!
[: 27: Normal: unexpected operator
Crap! its broken
Xlib:  extension "RANDR" missing on display ":0.0".

** (zenity:10165): WARNING **: Could not load notification icon 'update.png': Failed to open file 'update.png': No such file or directory
^C
------@----------:~$ 
[/q]

I am at my wits end using google to troubleshoot this really basic script.

Any help would be greatly appreciated

---

### Post by gzarkadas on 2010-06-14
You must put `$ans' in the test ( [...] ) brackets  inside double quotes, ie `if [ "$ans" = "..." ] ...'.

Also the path to `update.png' must be a full path; doing sudo changes you to root and also changes your home directory (if I remember well).

---

### Post by bodhi.zazen on 2010-06-14
I would suggest you write an xorg.conf with multiple server layouts.

I can not find a great web page to walk you though it, here is one : 

[http://wiki.osuosl.org/display/howto/Set+Up+Dual+Monitors+-+xorg.conf](http://wiki.osuosl.org/display/howto/Set+Up+Dual+Monitors+-+xorg.conf)

And this from the arch wiki

[http://wiki.archlinux.org/index.php/XLayout](http://wiki.archlinux.org/index.php/XLayout)

Do you see how they specify multiple layouts ?



Rather then booting to a graphical log in , you disable GDM . Log in and then user startx

startx --layout foo

ie specify your desired layout from the command line.

---

