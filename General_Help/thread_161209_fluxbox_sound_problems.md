---
title: "fluxbox sound problems"
date: 2006-04-16
forum: General Help
---

### Post by brantleyr on 2006-04-16
Is there any reason at all that sound would not work in fluxbox? my sound works perfect in gnome. I went to install fluxbox, booted up in fluxbox, and no sound works with it. Is there something im not doing correctly or a config file i need to edit, if so please help me. Thanks

---

### Post by hizaguchi on 2006-04-17
Maybe run alsamixer and make sure nothing is muted?  (If anything is, hit "m" to unmute it.  Most importantly "Master" and "PCM")

---

### Post by fotherington on 2007-04-16
I'm having a similar problem: sound plays flawlessly in Gnome (I was very impressed by the way I didn't have to do *any* configuration when I installed Ubuntu), but in Fluxbox the sound output is very low. I can hear it, if I turn up the alsamixer Master, PCM and Wave controls to the maximum, but then there's a loud hum. My soundcard is a Soundblaster Live!

...and just fixed it: plugged amp input into a different output on the back of the card, fiddled briefly with the alsamixer controls (volume is now controlled by Master and Wave Surround), and everything is working perfectly again. Strange that I had to do it, though.

If this hadn't worked, I was going to have a look at the relevant ALSA wiki entry: [http://alsa.opensrc.org/Emu10k1](http://alsa.opensrc.org/Emu10k1).

---

### Post by danish_demon on 2007-04-24
i'm glad i stumbled upon this thread, i was getting no sound in fluxbox but it turns out all i needed to do was load up alsamixer and unmute it, thanks.

---

