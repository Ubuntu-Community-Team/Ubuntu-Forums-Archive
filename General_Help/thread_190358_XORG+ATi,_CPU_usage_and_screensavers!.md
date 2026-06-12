---
title: "XORG+ATi, CPU usage and screensavers!"
date: 2006-06-06
forum: General Help
---

### Post by Onyros on 2006-06-06
Hi, guys... I'm having somewhat strange CPU usage problems with my laptop.

It has a 2.0GHz Pentium M (Sonoma), with 1GB RAM and an ATi X700 (with proper 3D acceleration through fglrx - 4250 fps in glxgears, 725 fps in fgl_glxgears).

I tried installing the i686 kernel, noticed no performance improvements whatsoever, but the laptop's fans were constantly in use, with just a few breaks in between. Therefore, I started checking out the cpu usage. I noticed that, strangely, xorg was taking up most of the resources... when idle! Even stranger, whenever I checked the system monitor out, especially its second tab where it displays graphs, cpu usage rode all the way up to 80%+.

Another strange thing I noticed, whenever I left the laptop idle for a bit, and the screensaver kicked in... the CPU throttled all the way up to 2 GHz, as if it were in great strain... and it was only the GLMatrix screensaver. Taking into account I think 3D acceleration is working well, this all added up to the total strangeness of these events.

I reverted to i386 kernel, and cpu usage is down, way down... but most of the symptoms persist. CPU usage is never as high as with the i686 kernel, but GLMatrix or other GL screensavers still present a problem, the system monitor graphs still spike my CPU usage, and the fans are still kicking in due to unusual cpu usage (lol, gotta love alliteration), but considerably less than with the i686 kernel, though.

Regarding games... I'm not much of a gamer, but I like my occasional pool game in between lumps of work. Foobillard is very choppy with this setup, but TORCS runs pretty well. I also find that strange, especially regarding the kind of results I'm getting from glxgears and fgl_glxgears.

I tried Sauerbraten... it starts with 150 fps, but whenever some other character gets in the same room... it drops as low as 10 or 15 fps, rendering the game unplayable even at 640x480.

I need your help and insight regarding this... What may be causing this? Is there anything I can do prevent this kind of irregular cpu usage, and have a better 3D performance? I'm most worried with cpu heating and the fans working a lot.
and
BTW, with gnome's monitoring applet, and the i386 kernel, the cpu usage is now 0% in idle, but all other problems I mentioned are still there.

---

### Post by Vati-Khan on 2006-06-06
check glxinfo everything is still ok after the kernel change, because even on my already ageing Radeon 9800 I get 

glxgears -printfps
32949 frames in 5.0 seconds = 6589.708 FPS
34173 frames in 5.0 seconds = 6833.864 FPS
34222 frames in 5.0 seconds = 6843.695 FPS
34286 frames in 5.0 seconds = 6838.197 FPS
34233 frames in 5.0 seconds = 6846.554 FPS
34310 frames in 5.0 seconds = 6834.818 FPS

and I think your Card is stronger than mine. Your CPU certainly is ;-)

did you upgrade or do a fresh install?

---

### Post by Onyros on 2006-06-06
Hmmm... that's even stranger :P
It was a fresh install, and I could swear I had this properly configured :P

I do get around 4250 fps in glxgears.

Guess I'm gonna reinstall the fglrx drivers clean first, and then I'll post any changes I noticed.

edit: Nope... reinstalled the ATi drivers using the second method listed here ---» [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

And I get the same glxgears results, 4250 fps tops. [scratch head mode on]

---

### Post by Vati-Khan on 2006-06-09
what's the output of glxinfo and/or fglrxinfo?

---

### Post by barakaspeed on 2006-06-13
Try this:

[http://www.ubuntuforums.org/showthread.php?t=194833](http://www.ubuntuforums.org/showthread.php?t=194833)

---

### Post by NewDisciple on 2006-06-13
Read this thread as well.
http://www.ubuntuforums.org/showthread.php?t=85917&highlight=386"]http://http://www.ubuntuforums.org/showthread.php?t=85917&highlight=386[/URL]

---

