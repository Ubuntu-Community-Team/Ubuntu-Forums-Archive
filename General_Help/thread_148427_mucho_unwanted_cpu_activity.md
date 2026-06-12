---
title: "mucho unwanted cpu activity"
date: 2006-03-22
forum: General Help
---

### Post by zi99y on 2006-03-22
Using KDE, when I close the lid on my laptop, when I open again I see the cpu activity was maxed out while it was down - the fan goes bull blast and kicks out  tons of heat!

Screensaver disabled, and in KLaptop the lid closed function is set to "off"

Any idea what could be causing it or how I can track it down - I close the lid to give the little bugger a rest!!!!:-k

---

### Post by SeanTater on 2006-03-23
Open K -> System -> Ksysguard. Go to the process table tab. Sort by system%. What ever has the highest number is the culprit. You can also try ```
top
``` in a terminal. It will give you an idea of what is going on. Also -- If you use the terminal option -- you can use ```
killall whatever
``` to stop every process named whatever.
[size=6]***_WARNING_***[/size]

Do not kill the following process names:


[LIST]
[*]Anything ending in /0
[*]khelper
[*]krfcommand
[*]startkde
[*]xorg
[*]kicker
[*]kdesktop
[*]klauncher
[*]kdeinit
[*]klogd
[*]syslogd
[*]anything starting with dbus
[*]x-session-manager
[*]It's not really a good idea to kill ssh-agent
[*]For gam_server, use ```
sudo killall -STOP gam_server
```
[*]hpiod
[*]kdesud
[*]dcopserver
[*]skim
[*]artsd
[*]kwin
[*]ksmserver
[*]kaccess
[*]kwalletmanager
[*]kbluetoothd
[*]klipper
[*]kded
[*]kmix
[*]knotify
[*]Anything with kio anywhere in the name
[*]cupsd
[*]acpid
[*]udevd
[*]cron
[*]dd
[*]sdpd
[*]mdadm
[*]shpchp_event
[*]pccardd
[*]khpshpkt
[*]Anything ending in _0
[*]most things ending in 0
[/LIST]

---

### Post by zi99y on 2006-03-23
thanks for the info, problem was that I couldn't see what was causing the activity because it only happened when the lid was closed, hence no screen!

Anyway I've fixed the problem by tweaking around. Seemed to be a setting in Kpowersave. General Settings > Lock screen on lid close > Select automatically. I unchecked this box and now everything is hunkydory.

Check another one off my fix list!

---

### Post by tjk on 2007-02-06
i have 100% CPU usage and it's CUPSD using most of it.  However it's my understanding from the prior message that I shouldn't kill this process (which seems to be doing nothing).  What should I do?

---

### Post by lucho64 on 2007-02-09
Same problem here. cupsd is running amok. And it's true that in general you shouldn't kill process without knowing what are you doing. OTOH, you can go to system->administration-services and uncheck the Printer service. Of couse, that means that you won't be able to print.
In my system, cupsd takes 100% cpu but I can still print or in general use the computer, is just that my einstein@home won't get any time to do any work! I've been doing some digging of my own to see what is the problem, I don't have a solution yet, but I think I have a description that might be useful to the cups folks, so I'll post a bug report.

---

