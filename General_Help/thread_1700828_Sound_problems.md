---
title: "Sound problems"
date: 2011-03-05
forum: General Help
---

### Post by Th0rn0 on 2011-03-05
Hey all,

Recently I have started using my netbook (Acer Aspire one D250) alot more due to travelling and I noticed that the mic didn't work. Headed to the Ubuntu forums and saw a thread about installing ALSA. So I did and now I have no sound.

From what I can tell ubuntu is no longer picking up my sound devices but I'm sure. Hence why I am here.

I need to get my sound working again (obviously) and then in turn get my mic working for mumble and other VOIP programs.

---

### Post by Zimmer on 2011-03-05
Only thing I can suggest (without chasing your tail on the many threads out there) is to open  a terminal and type 
alsamixer , and make sure you have the master/PCM/Mics etc activated (use Left-Right keys and up-down keys to modify the settings.)

---

### Post by Th0rn0 on 2011-03-05
no such file. Hmm that might be a problem

---

### Post by Zimmer on 2011-03-06
check in Synaptic PAckage manager that als-utils is installed... if not, install it..

---

### Post by Zimmer on 2011-03-06
Otherwise try around these...

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

