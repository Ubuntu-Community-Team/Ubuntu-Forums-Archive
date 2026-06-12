---
title: "Sound not responding"
date: 2010-07-29
forum: General Help
---

### Post by starplex on 2010-07-29
Last update. Can't turn my volume up! Why? I've been supporting the ubuntu foundation for 5 months now. I've installed my last updates. Why isnt the ****ing sound working properly?

---

### Post by chopinhauer on 2010-07-29
> **starplex said:**
> 
Why isnt the ****ing sound working properly?


Cursing doesn't help, but it's really effective in delaying answers.

Check if the process 'pulseaudio' is running. You can do it e.g. in a terminal with:
```
ps -C pulseaudio
```
If it is not the case (i.e. no line containing 'pulseaudio' is printed), try:
```
start-pulseaudio-x11
```
and look for errors.

---

### Post by starplex on 2010-07-30
Sorry bout the cursing. Was drunk.
I get this.
Home directory /home/whatever not ours.
Connection failure: Connection refused
And there is some kind of an error when the OS starts: a window appears saying that ICE something or other has an error.

---

### Post by dino99 on 2010-07-30
goto synaptic (system admin synaptic) and install: paprefs and gnome-alsamixer

then set your prefs with alsamixer: apps sound alsamixer

---

### Post by starplex on 2010-07-30
Would I be able to use the media buttons on my keyboard (volume keys)?

---

### Post by dino99 on 2010-07-30
you need to set your keyboard correctly: system prefs keyboard

choose the exact model of keyboard and define the third level in case

---

### Post by starplex on 2010-07-30
The whole sound system went crazy. It's repeating just once sound over and over. Can't watch anything.

---

### Post by dino99 on 2010-07-30
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by starplex on 2010-07-30
The OS just crashed. Could not log in, the monitor just kept turning off after the password. Reinstalled. Works fine now.
Thanks

---

