---
title: "Comp hangs on pressing alt-tab"
date: 2009-08-19
forum: General Help
---

### Post by topgun_tapan on 2009-08-19
The problem that I'm facing is that whenever I press alt-tab my jaunty installation hands. ctrl-alt-backspace doesnt work, mouse doesnt move, nothing works. I have to reboot my laptop. Based on the search results i got, I think it is a compiz problem but no working solutions.
Also, after enabling 3D windows and cylindrical desktop cube, whenever I rotate the cube using the mouse, my awn dock disappears, the title bar from all open windows disappear and all new programs i open are invisible.
Can anybody please help me out with this ? 
I was trying to convert some people in my hostel to use ubuntu and then this happened in between my demonstration. Not a very positive way to convert people to ubuntu :P.

The graphics driver I'm using is xserver-xorg-video-intel v2.8.0 and I'm using the kernel 2.6.30-10 both of which are from the repos

```
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main
```

This kernel and this driver have helped me resolve other issues like choppy videos, etc. So I hope these are not the problem.

---

### Post by P4man on 2009-08-21
you're using an pre release kernel and videodrivers :s
I know there have been issues with intel drivers, disabling compiz with jaunty, they did that for a reason. You probably installed that kernel and drivers to get around that, but all I can suggest is you file a bug report and revert to a stable kernel and/or videodriver. Even if that means no compiz for now. And persuade your hostel ppl not to buy integrated intel video ;)

---

