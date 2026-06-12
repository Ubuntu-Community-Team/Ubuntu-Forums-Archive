---
title: "Acer Aspire One - Microphone Not Working"
date: 2009-09-05
forum: General Help
---

### Post by s.fox on 2009-09-05
Hello,

I have installed Ubuntu Netbook Remix on my Acer Aspire One.  I can't seem to get the microphone to work with Skype or Sound Recorder.

I came across [this]("https://help.ubuntu.com/community/AA1/Fixes") page on the community wiki listing some fixes.  I attempted to follow the "Audio (Intel HDA)" guide but it does not seem to have done the trick.  It appears that /etc/modprobe.d/options.conf is no longer used,  though I have created the file manually and added in this:

```

options snd-hda-intel model=acer-aspire
```

I have also gone to sound preferences and changed Sound Capture to: 

HDA Intel ALC268 Analog (ALSA)

If anyone could please assist I would be extremely grateful.

Many thanks,

Silver-Fox

---

### Post by fandango11 on 2009-09-05
i had the same problem with my asus eee netbook and solved
it by removing pulseaudio which isnt supported until karmic arrives.
only thing is that removing pulseaudio also removes netbook remix.
anyway i did it and dont see any difference yet.......maybe the updates.....
evrything works now on skype and sound recording.....
look for more info before you take the plunge

---

### Post by s.fox on 2009-09-07
Bump for ideas :D

---

### Post by s.fox on 2009-09-10
3 day bump :(

---

### Post by greenfrog on 2009-09-10
The problem is the kernel.
You have to install 2.6.30 or above.

That fixed all the problems with my D150.

---

