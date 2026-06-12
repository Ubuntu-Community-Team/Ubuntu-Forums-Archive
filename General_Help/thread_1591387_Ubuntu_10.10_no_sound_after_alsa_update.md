---
title: "Ubuntu 10.10 no sound after alsa update"
date: 2010-10-09
forum: General Help
---

### Post by Jeanke on 2010-10-09
Hi,

I'm running Ubuntu 10.10 on an Asus UL20FT.
So far the sound was running "fine" (except for headphones and HDMI, but could live with these flaws so far).

Yesterday the Update Manager suggested an update of (if I remember correctly) the Alsa driver to version linux-alsa-driver-modules-2.6.35-22-generic.

Performed all suggested updates (there were some more, don't exactly remember which ones) but after reboot no sound at all anymore.

Can this be fixed, or eventually undo this update?
In synaptic history these updates seem not to show up...

Thanks.

---

### Post by Jeanke on 2010-10-10
Fixed, update came from PPA that was used to make my microphone working.
Removed PPA and uninstalled packages.
Sound is back, but no mic, headphones or HDMI sound.

---

### Post by Evil Dax on 2010-10-13
Installed fresh 10.10 today (had 10.04 before this)
I have a SPDIF for my digital audio (with amarok)
and use on-board for all the rest.
Now, whatever I do I can get only sound from SPDIF, so all Pidgin goes to my music amp.
Even VLC does not work anymore; HW:0,1 (default sound) goes to hw:1,1
:-(

---

### Post by staticsage on 2010-10-16
What PPA was it?

---

