---
title: "Restoring Sound Properties?"
date: 2010-07-24
forum: General Help
---

### Post by stuartwood89 on 2010-07-24
Hey guys.  I recently installed Ubuntu 10.04 onto my laptop, and I found that the sound quality was pretty poor.  After playing around with the settings in an attempt to fix things, it seems I no longer have any sound at all, and I can't remember the default settings.  I was wondering if there was a way in which I can restore all of the sound settings to the way they were when I installed Ubuntu.  I did try reinstalling PulseAudio, but that didn't seem to do anything.  Could anyone share some information on how to get things back to square one, so I can try and work out how to make my audio less fuzzy?

Thanks for reading.

---

### Post by stuartwood89 on 2010-07-24
Anyone?  I'd like to get this sorted and Google doesn't return anything useful.

---

### Post by lidex on 2010-07-24
What settings did you "play around with"?
Try this for starters:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by stuartwood89 on 2010-07-25
The settings I've changed were the profile under the Hardware tab (was originally on Analogue Stereo Duplex) and the connector under the Output tab (which I think was originally on Analogue Output / No Connector).  I've also run [COLOR="Red"]'sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common'[/COLOR] and under [Element PCM] I changed the volume value from merge to ignore.

Tried the command and it said that there's no such file or directory.

---

### Post by stuartwood89 on 2010-07-25
Ok I'm not entirely sure what did it, but it seems to be fixed.  For the benefit of anyone who finds this thread with the same problem, I'll list what I tried.

To remove the crackly audio, I opened the terminal and typed 'alsamixer'.
Using the arrow keys, I moved to PMC and lowered the value to 81, different PC's might require different levels.
Hit esc and it should be fixed.

It's not entirely perfect for me, but the crackling is gone and the audio is fine, except for a little background hiss if I use earphones.  I'll mark this as solved, and thank you lidex for your help.

---

