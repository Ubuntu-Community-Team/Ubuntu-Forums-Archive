---
title: "Sleep resume making login after upgrade"
date: 2011-07-12
forum: General Help
---

### Post by Mega_Hertz on 2011-07-12
Hi can someone help me.  I have upgraded from Ubuntu 9.x to 10.04 LTS

after the upgrade, my netbook goes to sleep in a short period of time and makes me login every time i resume.

This is very annoying as i have to wait for login and sometimes my wifi connection drops. I just quickly want to check my messages. The delay is annoying and has me using a windows (argh) laptop instead. i miss my ubuntu netbook.

i have tried adjusting power management setting to never go to sleep and adjusted some other power management module from the command line, but with no luck.

is there a way to reset the sleep pref's or any way to fix this.

Thank You

:D

---

### Post by macaholic on 2011-07-13
I'm not 100% sure if this is the case for 10.04, but I believe you can disable the lock by running "gconf-editor", going to apps>gnome-power-manager>lock, and unchecking the suspend box and  the use screensaver settings box.

---

### Post by Mega_Hertz on 2011-07-13
thank you. i tried the gconf-editor before but couldnt find the value i was supposed to edit. i think this may fix it. will update you after it goes to sleep thank you so much

: D

---

### Post by Mega_Hertz on 2011-07-13
Yeah, its fixed, again thank you so much macoholic.

---

