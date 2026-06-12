---
title: "Sound only in headphones with Sigmatel audio"
date: 2010-03-06
forum: General Help
---

### Post by abm2485 on 2010-03-06
I'm running a Dell inspiron 1501 laptop with a sigmatel stac 9200 sound chipset.

When I had ubuntu 9.04, I had sound no problem and when I upgraded to 9.10 I had sound for a little bit. Now the only way I get sound off my laptop is by plugging in my headphones. 

I've tried trouble shooting this a number of ways using the following links as the latest:

[http://ubuntuforums.org/showthread.php?t=614903](http://ubuntuforums.org/showthread.php?t=614903)

[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+head+phones](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+head+phones)

My question is...is there anyway to get sound on my laptop without having to go through headphones?

ps. I've installed and reinstalled ubuntu 9.10 and 9.04 and neither of them have sound.

---

### Post by agnes on 2010-03-06
Maybe you already tried,
but run 'alsamixer' and try to edit settings until it works (press M for unmute), and try the same with the 'pavucontrol' program (for the pulseaudio settings).

---

### Post by mikeTherob on 2010-03-06
I have had a similar problem myself, although my system seems pretty different from yours. I'm not sure if this will help you, but it's the way I managed to fix mine.

Under System>Preferences>Sound I just started playing around with the device settings. Since I don't much care for system sounds and such, I only changed Movie and Music sound playback. I didn't really know what to look for, so I just kept testing options from the dropdown menu (there were under 10 so it wasn't a painful process) until I found one that worked. HDA Intel STAC92xx Analog (055) was right for me, but I suspect that it will be different for you, if it's even the problem.

Hope that helps some, it's all I've got.

---

### Post by abm2485 on 2010-03-06
Yep, tried the alsamixer and the pavucontrol. Had to install the pavucontrol but regardless, everything is on full blast.

As for playing around with the preferences, there's nothing that says stac92xx analog. Was only analog stereo duplex, output, input and off.

Nothing brought the sound on.

I do thank you though, do appreciate it.

---

