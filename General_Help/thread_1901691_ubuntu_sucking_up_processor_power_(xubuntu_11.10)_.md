---
title: "ubuntu sucking up processor power (xubuntu 11.10) - running hot on dell laptop"
date: 2011-12-29
forum: General Help
---

### Post by aspidistra on 2011-12-29
here am running xubuntu 11.10 on a dell inspiron m5010 (triple core machine)

showing ~ 60% usage on two processors - nothing running

so now it's running hot

top shows "dbus-daemon" @ ~ 65% cpu 

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1695 bork       20   0 26136 2192  820 R   63  0.1   4:19.45 dbus-daemon        

ATI/AMD proprietary FGLRX graphics driver installed
(without installing the correct graphics driver the machine runs hot anyway)

shown here - screen shot of gnome-system-monitor / top (can scroll right to see system monitor)

newly installed xubuntu 11.10 here - whats up?

help help help 

[IMG]http://oi44.tinypic.com/2cnhzyw.jpg[/IMG]

---

### Post by houseworkshy on 2011-12-29
Running hot could be due to insulating dust so give it a clean.  Also try running a distro called puppy ( it runs in ram from the cd and won't touch your actual hd install unless you ask it to ) as a cross  check.  If that doesn't run hot then you know that you are dealing with a software problem.  You could also install sysinfo ( which is in the standard repositories ) then use it to post your system specs, that might  help people who know more than me to diagnose as it could be some hardware specific software bug.  There is also a small program in the repositores which gets specific cpu temperatures, lm-sensors, that could be handy for diagnostics too.  If you put it in just enter "sensors" without the quotes in the terminal to use it.  Sorry that is isn't actually a fix so much as some diagnostic advice but call it an elaborate bump. Good luck.

---

### Post by West201 on 2011-12-29
Your not alone I've experienced something similar, for now I would use Ubuntu 11.04 instead. It's more stable, uses less resources etc. 

Linux 12 (based on Ubuntu 11.10)also produces the same issues.

---

