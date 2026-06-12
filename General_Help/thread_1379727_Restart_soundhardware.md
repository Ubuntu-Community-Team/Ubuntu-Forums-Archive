---
title: "Restart sound/hardware?"
date: 2010-01-12
forum: General Help
---

### Post by Moozillaaa on 2010-01-12
Sometimes I can't get audio from online media players - youtube/BlueBox/etc, so I want to know the cli command for restarting the sound-playing process.

Like for networking - /etc/init.d/networking restart

Help?


edit:
I tried this:

sudo /etc/init.d/alsa-utils restart
but no-go.

Then this:

name@comp:~$ lsof | grep pc
gave no return.

Help?

---

### Post by adam814 on 2010-01-12
I guess the equivalent would be /etc/init.d/pulseaudio restart, but it might not give you the results you want.

I think old versions of flash bypass the sound server anyway (not sure how they do it, but I experienced it...couldn't get output on USB headphones because of it).

---

### Post by Moozillaaa on 2010-01-12
Thanks!

> **adam814 said:**
> I guess the equivalent would be /etc/init.d/pulseaudio restart, but it might not give you the results you want.
I'll try that one next time... I went ahead and restarted X, and got it back for now. (although local media files WERE playing/paused)


> **adam814 said:**
> I think old versions of flash bypass the sound server anyway (not sure how they do it, but I experienced it...couldn't get output on USB headphones because of it).
Makes sense; that would explain the 'no result' from the first command...?

---

