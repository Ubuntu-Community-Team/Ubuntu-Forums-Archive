---
title: "Tomboy startup glitch"
date: 2010-01-28
forum: General Help
---

### Post by varangian on 2010-01-28
I started using Tomboy notes to record useful bits of info and found it pretty useful so I added it to the startup applications to make it available on the taskbar from bootup. Initially this worked fine but after a while instead of just sitting on the taskbar the 'Search all notes' window is being instantiated on bootup, seemingly at random as it doesn't happen every time and I have yet to spot a pattern. It's getting kind of irritating to have to keep closing this.

I had a poke around in gconf-editor and the only relevant key I found was enable_startup_notes, although the function of this is apparently to re-open any notes left open at shutdown and I don't leave any such open. When I first checked I unset this and on looking again just now it appears to have been reset, which suggests Tomboy's behaviour is somewhat flakey. So my questions are:

a) Any way to fix this bug?
b) If no any recommendations for an alternative that is better behaved?

Thanks.

---

### Post by rocket16 on 2010-01-28
Is the version of your Tomboy stable?

---

### Post by varangian on 2010-01-28
> **rocket16 said:**
> Is the version of your Tomboy stable?

Should have mentioned that, it's V1.0.0 and and came as part of the apps with Ubuntu 9.10 so it's as stable as such things ever are. I notice from the Tomboy website that later versions are available but presumably they have yet to make it to the Ubuntu repositories.

---

