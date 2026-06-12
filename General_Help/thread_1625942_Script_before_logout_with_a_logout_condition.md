---
title: "Script before logout with a logout condition"
date: 2010-11-19
forum: General Help
---

### Post by funkwave on 2010-11-19
Hello! First of all, excuse my English. I'll try to explain the best I can.

Well, I want to do a script like the next one to avoid shutting down/rebooting/logging out the computer when either alarm is set or JDownloader is running. Instead of shutting down, it will turn off screen, HDs and audio (for JD case).

```
#!/bin/bash

hdDev="/dev/sdb1"



if [ -s $HOME/.config/alarm-clock/alarms.conf ]; then
	## Here any command to cancel the logout
	sudo umount $hdDev
	sudo hdparm -Y $hdDev
	gnome-screensaver-command --lock
	exit 1
elif [ "`top -b -n 1 | grep -c java`" = "1" ]; then
	## Here any command to cancel the logout
	amixer set Master mute
	sudo umount $hdDev
	sudo hdparm -Y $hdDev
	gnome-screensaver-command --lock
	exit 2
fi
```

1.- Where I have to put that script? I know that if I call it from */etc/gdm/PostSession/Default* is executed before that if I put it in */etc/rcX.d/*, but I think that putting in the first one is even late to cancel logout.

2.- Is there any command to cancel logout?

The idea is that the solution would work for any shutdown method, because I will like to use it for the case when I shutdown from XBMC (Media Center) and I think XBMC shutdown through "*dbus-send...*".


If needed: Ubuntu 10.04 [2.6.32-25-generic]

Thanks in advantage. ;)

---

