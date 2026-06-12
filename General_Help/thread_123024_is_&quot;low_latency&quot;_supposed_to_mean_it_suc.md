---
title: "is &quot;low latency&quot; supposed to mean it sucks?"
date: 2006-01-29
forum: General Help
---

### Post by jmxhgyZN8wK7 on 2006-01-29
hello... i'm using hydrogen 0.9.2-beta3 with ubuntu 5.10.

when i use hydrogen with alsa (i presume it's alsa, since qjackctl tells me jack is not running), everything sounds great.

when i use it with jack, though, i get lots of skipping, popping, volume fluctuation (click the instrument, hear it real soft, then click it again and it's loud)... basically, it's annoying.

isn't hydrogen supposed to work better with jack...? (when i use alsa, i get a bunch of weird error messages in red text in the command line - "[ERROR] Hydrogen [audioEngine_startAudioDrivers] Error starting audio driver [audioDriver::init()]" and line after line of "[ERROR] AlsaAudioDriver [alsaAudioDriver_processCaller] XRUN"

perhaps i need to change some settings?

can someone help me?

thanks.

(p.s. when i tried switching on "real time," thinking it might help, jack wouldn't even start.)

---

### Post by Ocxic on 2006-01-29
i believe low latency is a good thing, means that whatever your using is goin fast. example: in a game my prother play's having a latency of 25 is better then have one of 100. so unless I'm mistaken low latency is a good thing. tho in your cercumstances i could be wrong, so wait for someone to conferm this befor excepting it as fact. as for you problem unless you need jack for a specific reason go with ALSA scince it works fine.

---

### Post by mcduck on 2006-01-29
Latency is the delay between when you do something and when it happens. So, if you have 250ms latency, when you move a slider in Hydrogen it takes 1/4 of a second before that changes anything.

Or if you press a key in keyboard it takes 1/4 of a second before the sound comes out. And that would be too much to play anything. So lower latency is better. 

When I work with audio stuff I use Windows, With ASIO2 drivers for my sound card I get 4ms of latency. In linux I need 80ms for LMMS to work with ALSA.. I suppose Jack would work better, but I haven't found any easy starter guide to using/configuring it so Jack's still a bit of mystery for me.

---

