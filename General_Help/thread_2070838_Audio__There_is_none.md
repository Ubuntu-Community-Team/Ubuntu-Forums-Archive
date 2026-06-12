---
title: "Audio:  There is none"
date: 2012-10-13
forum: General Help
---

### Post by Notasoddingclue on 2012-10-13
No audio via the green socket at the back.  Tried the front one and that too is not responding.  So microphone not working.

Any ideas on how to get it to work?

---

### Post by pqwoerituytrueiwoq on 2012-10-13
what do these commands give you?
```
lspci | grep Audio
```
```
aplay -l
```

---

### Post by Notasoddingclue on 2012-10-13
In terminal, nothing.  Aplay -1 is not recognised.  I downloaded Gnome alsa mixer and the microphone works from the front but not through the built in audio.  Audio comes through the front but not on Skype.  From the rear it does nothing at all.

---

### Post by pqwoerituytrueiwoq on 2012-10-13
it is case sensitive and that is a L not a one

---

### Post by Notasoddingclue on 2012-10-13
Ahhh.  My bad.

I get this:

>  **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by pqwoerituytrueiwoq on 2012-10-13
and the other command i posted...
BTW that is a pipe (shift+backslash) not a L or a one

---

### Post by Notasoddingclue on 2012-10-14
I get nothing from it.  It just returns back to prompt.

---

### Post by CCgirl6690 on 2012-10-14
i remember fixing it like this..........

startup applications...
add....
in command box  type in "/usr/bin/pulseaudio"
reboot and all good

---

