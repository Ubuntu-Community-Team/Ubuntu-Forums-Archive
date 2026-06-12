---
title: "Rhythmbox and movieplayer doesnt work after using flash on firefox and vice-versa"
date: 2009-08-20
forum: General Help
---

### Post by countryjake on 2009-08-20
I did a large amount of research and see the problem occuring in older versions of ubuntu, however, I am running Jaunty and this bug page: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/239757](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/239757) says that this issue was solved in Jaunty, but I beg to differ.

I tried to follow the directions they gave, installing libflashsupport, but it is obsolete, and it suggested installing flashplugin-nonfree-extrasound
So i went ahead and first installed flashplugin-nonfree, which also installed flashplugin-installer, which i thought was already installed as flash worked, but apparantly not. Then i installed flashplugin-nonfree-extrasound and attempted to play sound on youtube and rhythmbox simultaneously and it did not work again. It also does not work when flash is used before rhythmbox, then pausing flash and trying rhythmbox, and vice-versa!
I am currently running Kernel 2.6.28-15-generic, and have 2.6.28-14-generic, 2.6.28-13-generic, and 2.6.28-11-generic installed, and none of which work as well.
I do not know if something i installed caused the problem as i did not use rhythmbox until recently since i am on vacation and dont have speakers to hook my iPod up to.
Furthermore, I believe i have the newest version of ALSA installed, because without it my built-in microphone doesnt work

This problem ALSO occurs when i use movieplayer, however instead of not playing at all, the movie plays extremely slowly, so slow that over 30 real seconds=1 second in the movie, leading me to believe this is what is happening in rhythmbox as well, and it is extremely annoying as i have just began to use it often to watch my favorite tv shows, etc.

---

### Post by Vaphell on 2009-08-20
32 or 64 bit?

---

### Post by countryjake on 2009-08-20
32-bit

---

### Post by countryjake on 2009-08-20
UPDATE:
Ok it seems as though if flash player of any kind starts (like facebook chat or anything) then sound for anything stops working, ie pidgin, thunderbird, etc. and vice versa!
this is an extremely annoying problem and i would really like to have it fixed! someone please help!!

---

### Post by majamba on 2009-08-20
if the sounds stops working try reloading the alsa drivers

---

### Post by countryjake on 2009-08-20
how would i go about doing that? i forget how i upgraded the drivers in the first place, possibly there are newer ones i could install as well??

---

### Post by countryjake on 2009-08-20
PROBLEM FIXED!!!
i went to system, preferences, sound
then i changed all the options to ALSA and now i have no problems whatsoever

basically it was using Pulseaudio and it was screwing up everything

---

### Post by mellery on 2009-12-06
I have this exact same problem, its very annoying! I dont have the option of selecting also in the sound preferences?  Maybe it was changed in karmic, but how can I fix this?

---

