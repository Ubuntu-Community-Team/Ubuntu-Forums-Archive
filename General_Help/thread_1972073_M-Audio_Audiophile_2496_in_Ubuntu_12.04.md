---
title: "M-Audio Audiophile 2496 in Ubuntu 12.04?"
date: 2012-05-03
forum: General Help
---

### Post by Igorpan on 2012-05-03
Hello! I have soundcard named in the title and I can't make it work. Ubuntu obviously recognizes it, but I can't hear any sound coming out. I had problems with this soundcard in 11.10 and 10.04 too (which i've been using prior to 12.04),[ this]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/30") seemed to fix it. However, now it doesn't.

---

### Post by Igorpan on 2012-05-03
Bump, I really need help with this guys as I have no idea what and how to search for ? And using Ubuntu without sound is just......meh....i won't settle for that :(

---

### Post by oblio9 on 2012-05-07
I have the same hardware and same problem if anyone has any insights I would appreciate it as well. Thanks!

---

### Post by v0idnull on 2012-05-12
same card. no audio whatsoever.

tried various tricks such as running alsamixer to ensure nothing is muted, pavucontrol checks out...

I don't know what to do next.

---

### Post by jeppe_99 on 2012-05-17
I am on 11.10 and also have problems with the card. In my case it plays everything a little too fast. I use the tool envy24control to set the Master Clock to 44100. Whenever I reboot the machine it gets reset to 48000. Most annoyning, but with this workaround it works. 

Maybe it can help you to? It is not installed by default, but if you use Synaptic, you can search for it. It is in the alsa-tool-gui pack.

Best regards
Jeppe

---

### Post by oblio9 on 2012-06-10
Okay, got it. Made sure that no other audio devices were on or connected (built in audio and disconnected webcam as it has a mic) and tried this:
[http://www.geoffke.be/nieuws/5/](http://www.geoffke.be/nieuws/5/)
Audio works fine now. Also able to record.

---

### Post by Ruhani04 on 2012-10-06
Just install envy24 control via software center.
Open after installation and go to "analog volume" tab. Move the two volume sliders to your liking and sound should work fine.
I have been doing this several times in different Ubuntu/Lubuntu/Xubuntu installs.

:guitar:

---

