---
title: "Revisiting: &quot;Doubleclicking with a Wacom stylus doesn't work&quot;"
date: 2009-12-29
forum: General Help
---

### Post by jmc_tagger on 2009-12-29
Couldn't get xsetwacom (or xorg.conf mods) to work to set button-2 on my Wacom stylus to double-click.

An archived thread titled "Doubleclicking with a Wacom stylus doesn't work" at [http://ubuntuforums.org/showthread.php?t=418203](http://ubuntuforums.org/showthread.php?t=418203) was unresolved, and a few other threads covered the same topics, but none seemed to rank as high on google.  Most notably, the official bug report at: [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/112310](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/112310)

Anyway, I've found a workaround and thought it might be helpful to share with others.  The core problem still exists (see the bug for more details).  Until it's fixed, this worked for me:

**Background:**

See [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom) for general instructions on xsetwacom (and xorg mods)
See [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/112310](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/112310) and others for bug description (even the 196609 trick didn't work)

** Resolution:**
I followed [http://ubuntuforums.org/showthread.php?t=316441](http://ubuntuforums.org/showthread.php?t=316441) and did the following to "emulate" a double-click with button-2:

First of all, set button2 back to button-2 if modified:
  > xsetwacom set stylus "button2" "button 2"

Install stuff (as root) (sorry, I'm a debian guy, but the original thread was in this ubuntu forum, so I thought I'd post my resolution here; modify as you wish):
  > aptitude install xautomation xbindkeys

Note that xautomation includes xte, which is what we use below.

create/edit ~/.xbindkeysrc for user:
  > 
"/usr/bin/xte 'mouseup 2' 'mouseclick 1' 'mouseclick 1' &"
  b:2


start xbindkeys, to test:
  > xbindkeys -n -v

try button-2, see if it works.  If so, add
>    xbindkeys &
to your x startup script, whatever it might be (e.g., for me, it's ~/.config/openbox/autostart.sh), and you're good to go.

Hope it works for you as it is for me.

---

