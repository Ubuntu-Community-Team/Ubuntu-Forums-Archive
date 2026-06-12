---
title: "Mplayer does not play *.ogg video files"
date: 2006-06-10
forum: General Help
---

### Post by blackjack6.21.91 on 2006-06-10
But my other video players (totem, realplayer) do.  I really have a preference for mplayer, so I would like to be able to use it to play my files (it's also my default player, so I don't want to confuse the other people who use this computer with errors).  When i run it in a terminal the return is:

> MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP/XP-M Barton,Thorton (Family: 6, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.



91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /home/cinmas/Desktop/documents/ben/videos/aqua.
File not found: '/home/cinmas/Desktop/documents/ben/videos/aqua'
Failed to open /home/cinmas/Desktop/documents/ben/videos/aqua

Playing /home/cinmas/teen.
File not found: '/home/cinmas/teen'
Failed to open /home/cinmas/teen

Playing /home/cinmas/hunger.
File not found: '/home/cinmas/hunger'
Failed to open /home/cinmas/hunger

Playing /home/cinmas/force/aqua_teen_hunger_force_vol4-01.ogg.
File not found: '/home/cinmas/force/aqua_teen_hunger_force_vol4-01.ogg'
Failed to open /home/cinmas/force/aqua_teen_hunger_force_vol4-01.ogg


Now I realize that it asks me to try adding 
echo 1024 > /proc/sys/dev/rtc/max-user-freq 
to my startup scripts, but I realize that those are not specific instructions and there are probably much better steps to take when running Ubuntu.

---

### Post by antidrugue on 2006-06-10
[QUOTE=blackjack6.21.91]
Now I realize that it asks me to try adding 
echo 1024 > /proc/sys/dev/rtc/max-user-freq 
to my startup scripts, but I realize that those are not specific instructions and there are probably much better steps to take when running Ubuntu.[/QUOTE]

The official way to do this is to add a line like that:
```

dev.rtc.max-user-freq = 1024

```

at the end of the file */etc/sysctl.conf*, and then reboot, as explained here:
[http://www.ubuntuforums.org/showthread.php?t=85190](http://www.ubuntuforums.org/showthread.php?t=85190)

---

### Post by blackjack6.21.91 on 2006-06-10
Alright.  Thank you.  I'll probably add another post later to see if that resolves everything.  I hope it doesn't slow me down too much though.. not exactly sure what the command does..

---

