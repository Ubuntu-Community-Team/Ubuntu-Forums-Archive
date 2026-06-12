---
title: "ubuntu went into low graphics mode mid-session"
date: 2012-02-27
forum: General Help
---

### Post by rmetzger on 2012-02-27
While working through a microphone issue my wife's ubuntu machine (it doesn't work in skype) the computer  went into a low graphics mode and is apparently not loading the correct graphics drivers.  I've not been able to get it back into a gui since.

Reboots and recovery attempts have not resulted in any success, reboots hang after a battery check (seems to be trying to load alsa).  This may be a part of the root cause as the last thing I was working on prior to the low graphics mode was installing the gnome alsa mixer and plugs ins.

the machine is an HPCQ61-420US with a radeon HD 4200 video card

any thoughts?

---

### Post by raja.genupula on 2012-02-27
Have you tried by reinstalling the graphics drivers ?

---

### Post by rmetzger on 2012-02-27
yes - it still hangs during startup

just after it lists "checking battery state" it hangs.
a ctrl-alt-delete reboots with the following message:
tty4 main process killed (1082) killed by TERM signal
tty5 " "
tty2 " "
 
and so on until it reboots

---

