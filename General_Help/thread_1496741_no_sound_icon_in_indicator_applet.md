---
title: "no sound icon in indicator applet"
date: 2010-05-29
forum: General Help
---

### Post by alem189 on 2010-05-29
Hello - Even though I have all the all the other icons(network, battery, etc.), the sound icon doesn't seem to show up. Does anyone know what could be causing this?

And sorry, I meant notification area, not indicator applet.

EDIT: Just to clarify, the sound works perfectly well, as does everything else. I can still change my sound using the keyboard, but I have to use a fn + key combination, and that gets tedious, especially when I have to get the volume up several notches.

---

### Post by alem189 on 2010-05-29
*bump*

---

### Post by Joe Awsome on 2010-05-29
try right clicking the task bar (the thing that desplays windows and icons) and adding a volume control applet. I don't know too much about gnome seeing how I only tried it once, could be wrong but everything else tells me thats how it works. Can you get sound on your multimedia and internet? If not Ubuntu probably hasn't detected a sound card, or hasn't loaded an audio driver for it.

---

### Post by alem189 on 2010-05-29
I've heard that in earlier versions of ubuntu, there were different applets for sound or network, but it seems like now they are all included in indicator applet. Thanks though:)

---

### Post by alem189 on 2010-05-29
See my earlier edit, I probably should originally said that.

---

### Post by alem189 on 2010-05-29
*bump*

---

### Post by bildr on 2010-05-29
I had the same issue and it came and went.  I pinned system->preferences->sound to the taskbar instead.

I think it has to do with applets fighting over which one gets loaded first and the sound applet timing out.

I never really fixed it, but this workaround works for me.  It was also necessary because flash couldn't tell when I plugged in headphones.

---

### Post by lidex on 2010-05-29
Do you have a 'System>Preferences>Sound' applet?

---

### Post by alem189 on 2010-05-29
Got it, thanks for the explanation and workaround.

---

### Post by squashwa on 2011-02-15
You are probably missing the "indicator-sound" package. I had this problem after reinstalling pulse audio.

1) ```
sudo apt-get install indicator-sound
```2) Remove the indicator applet from the panel, and then re-add it.

---

