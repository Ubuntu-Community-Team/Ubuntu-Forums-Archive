---
title: "No sound after 2.6.28.14 update"
date: 2009-07-30
forum: General Help
---

### Post by Patricrawley on 2009-07-30
I had everything working but my microphone on 2.6.28.13 and when the update came for 14 nothing works. I have booted back into 13 and my sound still works. I have tried to reinstall alsa in 14 but nothing happened. I am running 9.04 amd64 on an acer 8930g,

---

### Post by fillintheblanks on 2009-07-30
me too the new update reset my sound settings


I check them manually they work fine now,

turning on the 'analog/digital output jack' switch did the trick for me.

---

### Post by Patricrawley on 2009-07-30
I don't think I have that switch

---

### Post by Jimstehrman on 2009-07-30
I've always had trouble with my Acer and sound in Ubuntu, so I finally I got an external sound card and it works more often, I find you have to try out various combinations of drivers in the sound options menu and one will eventually decide to work, other than that it still mystifies me.

---

### Post by Patricrawley on 2009-07-30
I had it working until this kernel update though, I guess I'll just use the old kernel for now.

---

### Post by Patricrawley on 2009-08-12
Is there a fix for this yet?

---

### Post by RedSingularity on 2009-08-12
I had the same problem.  It turns out ALSA and pulseaudio were having problems with each other.  I removed pulseaudio and chose ALSA in the sound setup.  System>Pref>Sound.  Works great now.

---

### Post by pizza-is-good on 2009-08-12
> **Patricrawley said:**
> I had it working until this kernel update though, I guess I'll just use the old kernel for now.
 
I'd do that. Wait until next kernel comes around and try it then.

---

