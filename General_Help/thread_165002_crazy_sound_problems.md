---
title: "crazy sound problems"
date: 2006-04-23
forum: General Help
---

### Post by lopzided on 2006-04-23
this problem is driving me nuts...i can't find the answer anywhere!

a lot of times, when certain commands are run from console, i get this:

```
juztin@ubuntujuztin:~$ sudo gedit /etc/default/prelink
- using device default
- using device default
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.
Audio device open for 48Khz, stereo,16bit failed
Trying 22.05Khz, 8bit stereo.
Audio device open for 22.05Khz, stereo, 8bit failed
Trying 44.1Khz, 16bit mono.
Audio device open for 44.1Khz, mono, 8bit failed
Trying 22.05Khz, 8bit mono.
Audio device open for 22.05Khz, mono, 8bit failed
Trying 11.025Khz, 8bit stereo.
Audio device open for 11.025Khz, stereo, 8bit failed
Trying 11.025Khz, 8bit mono.
Audio device open for 11.025Khz, mono, 8bit failed
Trying 8.192Khz, 8bit mono.
Audio device open for 8.192Khz, mono, 8bit failed
Trying 8Khz, 8bit mono.
Sound device inadequate for Esound. Fatal.

```

i don't know if this is related or not, but the sounds that usually play when ubuntu starts up (the bongos at login and the atmospheric sound during the splash screen) no longer work.

i have been searching for days and can't find the answer to this, please help!

---

### Post by thunderduck3141 on 2006-04-23
did u disable the sound server?
go to System>Sound
make sure it is enable
reboot
find out what ur soundcard supports (OSS and/or Alsa)
and make sure to enable the correct one (if both i recommnd Alsa)
double check and see if the sound is mute/off (little icon near the clock on upper right corner)

---

### Post by thunderduck3141 on 2006-04-23
also, make sure that the correct bit is set, try setting it to 24

---

### Post by lopzided on 2006-04-23
all sound works fine, except startup sounds....sound is enabled....my soundcard supports alsa and it is set to alsa in system/pref/multimedia selector...

i think its a config problem

---

### Post by rts on 2007-05-03
Just today I've started suffering the same problem, and I have no idea how or why this suddenly broke.

---

