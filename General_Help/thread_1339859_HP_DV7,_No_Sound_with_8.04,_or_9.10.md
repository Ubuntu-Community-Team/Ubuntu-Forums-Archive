---
title: "HP DV7, No Sound with 8.04, or 9.10"
date: 2009-11-28
forum: General Help
---

### Post by Spoooolin on 2009-11-28
So, i LOVE ubuntu, minus the no sound issues.  I first installed 9.10  Tried following along some steps I found while doing a google Search, and had no luck.   After reading a few threads on here, I realzied, its kind of a common prob. so I figured I would load 8.04 and see what luck that brings me, and sure enough, No sound.  No start up sound, no sound while watching youtube videos, and that was the same with both versions.

I have a new HP dv7 3065dx    Now, I am a N00b to all this, So ANY help I get will be GREATLY apperacited, Please, feel free to dummy down the advice, so I can understand it haha.  

Hope you guys can help!!  Thanks!


Also, I would LOVE to have 9.10 back on here, with sound, BUT, if thats not an option, 8.04 will work

---

### Post by Spoooolin on 2009-11-28
bump!1

---

### Post by coteyr on 2009-12-04
1) Get hda-verb utility (Do a goole search for it) and install it.

2) Add the following to the /etc/rc.local startup script:

/usr/local/sbin/hda-verb /dev/snd/hwC0D0 0x01 SET_GPIO_MASK 3
/usr/local/sbin/hda-verb /dev/snd/hwC0D0 0x01 SET_GPIO_DIRECTION 1
/usr/local/sbin/hda-verb /dev/snd/hwC0D0 0x01 SET_GPIO_DATA 1 

Make sure none of the volume settings are low or muted.

Reboot. You should now have sound.

from [http://www.kr.xemacs.org/pub/linux/kernel/people/tiwai/misc/hda-verb/](http://www.kr.xemacs.org/pub/linux/kernel/people/tiwai/misc/hda-verb/)



I found that laying around somewhere it's not my fix.

---

### Post by coteyr on 2009-12-04
BTW you don't need to reboot, add the lines to the file then just run the commands.

---

