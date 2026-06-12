---
title: "How to switch Off monitor in U10.10 ?"
date: 2011-02-04
forum: General Help
---

### Post by kapetr on 2011-02-04
Hello,

if I use **xset dpms force off**, then the monitor sleeps only few seconds (sometimes miliseconds :-) and then goes up again without moving mouse, ... (by itself)

But it is no system problem - if the monitor is switched off from GNOME - e.g. after 10 min, then it stays sleeping up to some action (mouse, keyboard, ...).

**Why do it not work if switched off manually ?!**

Thanks for every help

--kapetr

---

### Post by davidmohammed on 2011-02-04
have you tried

sleep 1 && xset dpms force off

?

---

### Post by kapetr on 2011-02-05
It helps not.

Why should ? Especially by "autowakeups" after cup of seconds.

Thanks for replay

--kapetr

---

### Post by davidmohammed on 2011-02-05
ok - try forcing the screensaver  to kick in as well (remember to set the screen saver to "black" not a random pattern)

sh -c "xset dpms force off && gnome-screensaver-command --activate"

---

### Post by kapetr on 2011-02-07
It is a clever idea. 

I also in fact think too, that the problem is by trying of GNOME at all costs keep control over the PM and that it maybe may prevent sleep (e.g. from X server) by "wakeup pings" until it self decides to suspend monitors.

But - this solution do not helps too. As I have try it, after few minutes I had return - the monitors LEDS was in "power on" - just the screens was blanked  - by screensaver.

What would probably help is - to know GNOMEs command to sleep monitors or to disable its autocracy.

--kapetr

---

### Post by eastwater on 2011-02-07
```

#!/bin/bash
gnome-screensaver-command -l
sleep 1
xset dpms force off
exit
```I put this script in /usr/local/bin and summon it with a keyboard shortcut in preferences. Works great. Just got to figure out how to turn off my keyboard backlighting at the same time.

Hope it helps.

---

### Post by kapetr on 2011-02-09
1. to avoid any HW issues I had install U10.10 also to another PC - with same results.

2. I had try **eastwater**s solution with exact same result as described in my previous post.

Are you really sure, it works for you ? 

Take again one look to LED colour of yours monitor when you thing it is "sleeping"! If it goes (after cup of seconds) to the same as when "on" - then the screen is just blanked by screensaver, NOT sleeping. You will also see, that after mouse move the password dialog appears immediately. By sleeping (analog) monitor it would take some time to light up.

thanks

-kapetr

---

### Post by kapetr on 2011-02-18
nobody knows or nobody needs ?

---

### Post by cokicd on 2011-02-18
> **kapetr said:**
> nobody knows or nobody needs ?

I know a way:

1) **sudo visudo**
add this to the end of the file (replace with your username):[I][B]
yourUserName[/B][/I] ALL = NOPASSWD: /usr/sbin/vbetool

2) Assign this command to a keyboard shortcut to turn off the monitor:
**gksu vbetool dpms off**

3) Assign this other command to a keyboard shortcut to turn on the monitor:
**xset dpms force off**   *(yes, off)*

That should do the trick

---

### Post by kapetr on 2011-02-19
> **cokicd said:**
> I know a way:
...
That should do the trick


THANK YOU !!!  It works :-)

BTW: Don't you have Idea how to put Ubuntu into ACPI S1 (sleep) mode ?
Maybe it would be good solution, but GNOME let me chose only between S3 (STR) and S4 (STD). And pm-utils don't offer S1 too ?!

And even by S3 is also disk switched OFF, what is sure not well for his health by short sleep times (less then hours). 

**-----**

To make OFF/ON with just one GNOME shortcut I modified the action to:
> 
bash -c 'if [ -f /tmp/monitor_OFF ] ; then xset dpms force off; rm /tmp/monitor_OFF; else sudo vbetool dpms off; touch /tmp/monitor_OFF; fi'


--kapetr

---

### Post by cokicd on 2011-02-19
> **kapetr said:**
> 
BTW: Don't you have Idea how to put Ubuntu into ACPI S1 (sleep) mode ?


No, I don't know how to do that.

---

### Post by kapetr on 2011-02-25
Hello,

to make ACPI S1 working, I made my own little hack.

See my other thread:

[http://ubuntuforums.org/showthread.php?t=1679036](http://ubuntuforums.org/showthread.php?t=1679036)

--kapetr

---

