---
title: "sound system"
date: 2010-09-24
forum: General Help
---

### Post by kendubay on 2010-09-24
i have a dell latitude D510 that has ubuntu installed on it, for some reason today the speakers stopped working, this morning they worked when using vlc player but the we started up mixxx dj software, but when trying to open it showed the message sound device busy, mixxx cannot access the sound device, and after that the speakers have not been working at all in any software

i need help asap

thanks in advance

---

### Post by lkjoel on 2010-09-24
> **kendubay said:**
> i have a dell latitude D510 that has ubuntu installed on it, for some reason today the speakers stopped working, this morning they worked when using vlc player but the we started up mixxx dj software, but when trying to open it showed the message sound device busy, mixxx cannot access the sound device, and after that the speakers have not been working at all in any software

i need help asap

thanks in advance
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by kendubay on 2010-10-02
i just get a whole lot of errors when i try this, any other ideas? or am i just doing something wrong?

---

### Post by jalampi360 on 2010-10-02
This will remove pulseaudio and alsa sound from your system and add oss sound. Providing you do this correctly (Just follow the directions) you will have sound. The down side to this you will not have startup sound, and you will not be able to access the sound option in the system/preference menu, since they all depend on pulseaudio.

This solution really does not correct the problem since it does not leave your system intact. Does anyone have a more system friendly solution for this?

---

### Post by luctor on 2010-10-02
start mixxx
open Options -> Preferences 
look for soundhardware -> select pulse in the drop down menu

---

