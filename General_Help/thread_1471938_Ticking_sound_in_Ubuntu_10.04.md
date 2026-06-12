---
title: "Ticking sound in Ubuntu 10.04"
date: 2010-05-03
forum: General Help
---

### Post by kenweill on 2010-05-03
I've got this very annoying ticking sounds in my Ubuntu 10.04 installation.
Ticking sound comes out when im playing a movie (always), when playing flash games with firefox(always), when closing browser (sometimes, 1 tick sound), when scrolling this forum using my mouse scroll(sometimes).

I've found some threads in this forum that solves the ticking sound for ubuntu 9.10 but it doesn't work with 10.04 as there's no "power_save" option found in "/etc/modprobe.d/alsa-base.conf", here in ubuntu 10.04.

i've tried lowering/disabling volumes (input) with alsamixer, still, it doesn't solve the problem.

Been using this same machine with Ubuntu 8.04 (dual booted with winxp) and got no problems with sound ticking. I have tried dual booting 8.04 with win7 before and win7 also got this ticking problem so i go back to dual booting winxp and 8.04.

just this morning, i ditch winxp and 8.04 installing 10.04 in this drive, but got this ticking problem.

What else can I do with this problem?

---

### Post by kenweill on 2010-05-04
~bump~

Additional info of what i've tested so far.

Decreasing volume level to 0, i still hear ticking sound, while playing a movie.
Mute all, is the only option to stop the ticking. Un-mute makes the ticking comes back.

I filed a [bug report]("https://bugs.launchpad.net/ubuntu/+bug/574900") regarding this.

---

### Post by kenweill on 2010-05-05
~bump~


Additional info:
No sound ticking when playing music with Rhythmbox.
No sound ticking when when playing a movie with VLC media player. Ticking comes back when playing a movie with the default Movie Player.
Starting a movie with VLC, i hear ticking in a few seconds then disappear.

---

### Post by pqwoerituytrueiwoq on 2010-05-05
i have seen that happen with videos occasionally on Ubuntu 9.04
it was not something you could miss
i simply restarted the player to fix it

---

### Post by kenweill on 2010-05-06
> **pqwoerituytrueiwoq said:**
> i have seen that happen with videos occasionally on Ubuntu 9.04
it was not something you could miss
i simply restarted the player to fix it

there was a permanent fix for that for 9.04 but is not applicable with 10.04. it was editing the file "/etc/modprobe.d/alsa-base.conf". But with 10.04, it has different content. Not the same content with 9.04.

---

### Post by kenweill on 2010-05-06
~fixed~

by an update

---

