---
title: "Sound does not work (HDA Intel)"
date: 2009-12-24
forum: General Help
---

### Post by alexplAnTe on 2009-12-24
Hey everyone!

Sound is not working on my Xubuntu 9.10 desktop :confused:. Why? I don't **** know. 
My sound card is an onboard Intel HDA on a Asus P5KC motherboard. When i click on the mixer, I can't choose my sound card. I have 2 choice : Playback Dummy Output (PulseAudo mixer) and Capture Monitor of dummy output. When I sudo alsamixer, the name of my soundcard is there (Intel HDA) and even if I crank the volume up in all those weird color things (volume bar), i can't ear anything ... dammit ! 

Help me please :P
Tank you and have a good Christmas:P

*** EDIT : Wow i logged in as root and the sound worked ! It does not work on a regular user ! On root I had the choice of HDA Intel ALSA and HDA Intel OSS. So this mean that it is a permission problem ***

---

### Post by alexplAnTe on 2009-12-24
Solved it !

I added my username in "/etc/group" at the "Audio" line and then I "sudo chmod 666 /dev/dsp"

:guitar:

---

### Post by RedSingularity on 2009-12-24
Try uninstalling pulseaudio and logging in again.

EDIT:  Whoops too slow.

---

