---
title: "HDMI Sound In 11.10"
date: 2012-03-14
forum: General Help
---

### Post by Andysoldier on 2012-03-14
I have asked about this in Multimedia and Sound but to no avail.

OK i have of course seen many threads on this but i have tried all of  the suggestions, gone through the "comprehensive guide..." *and *because of what has happened i believe someone may be able to help and therefore help many others.
 
My PC is connected via HDMI to a TV. If i hook up my headphones to the  back of the PC i hear everything. If i take them out i only hear the  sound from games (Eternal Lands and Glest).
 
So, those games must be activating/loading the correct sound driver  right? I've looked for any hints of what they are loading in config  files etc but can't find anything.

Banshee plays audio, VLC plays audio and Epiphany web browser plays audio.

Firefox and Chromium don't.
 
Grateful for any help.
 
Ubuntu 11.10 64 bit.
Radeon 6300 on board graphics.

---

### Post by zero2xiii on 2012-03-14
Hay,

Open up your sound preferences (Type "sound" in the panel and you should find it)

Make sure your output is set to "Digital" or "HD Media" or "HDMI" or such... Most guides on the internet asume you have already checked this.

Just stating the obvious since its sometimes overlooked.

Cherz

---

### Post by Andysoldier on 2012-03-14
Thanks for the reply zero.  Yes, in sound, hardware there are 2 devices - HDMI output and analogue stereo.

The only thing that isn't producing sound now is Mozilla Firefox (my browser of choice because of BBC iPlayer, ITV player etc) and the O/S itself.  *Although* i *can* hear audio on Firefox if i plug my headphones into the jack on the back of the PC.

---

### Post by pqwoerituytrueiwoq on 2012-03-14
File:
[FONT=Courier New]/etc/asound.conf[/FONT]
Content:
```
pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}
```That fixed it for my mom (lucid 64bit/nvidia gt 430) [[related thread](http://ubuntuforums.org/showthread.php?t=1926721&page=2#19)]
you may need to log out and in or reboot for it to take effect

---

### Post by Andysoldier on 2012-03-14
Well i can't quite believe it pqw, that worked!  I shall post that on my other thread and put it to solved.

Thanks very much!

---

### Post by Andysoldier on 2012-03-14
Could someone just explain what the pcm and the ctl commands are?

Rather than just getting sound and being happy i'd like to learn from this.

Thanks very much.

---

