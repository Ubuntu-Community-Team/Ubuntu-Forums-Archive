---
title: "Mic not working"
date: 2009-09-13
forum: General Help
---

### Post by nerdking on 2009-09-13
hey just got back on ubuntu after awhile away and it seems that my mic is not wanting to work with ubuntu right now, my knowledge on this subject is a bit rusty and i would greatly appreciate any help.

---

### Post by jbrown96 on 2009-09-13
Check if your mic channel is muted. ```
alsamixer
``` If that only shows a single "pulseaudio" channel, then exit. System--->Preferences--->sound, change all the options to ALSA. Good idea to reboot, then try alsamixer again.

---

### Post by nerdking on 2009-09-13
[IMG]http://i31.tinypic.com/208i80z.png[/IMG]

i got this, any idea whats wrong?

---

