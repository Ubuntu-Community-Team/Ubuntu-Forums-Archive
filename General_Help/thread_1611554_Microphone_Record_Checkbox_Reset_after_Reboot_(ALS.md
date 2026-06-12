---
title: "Microphone Record Checkbox Reset after Reboot (ALSA MIXER)"
date: 2010-11-02
forum: General Help
---

### Post by vsh3r on 2010-11-02
Ubuntu will automatically reset the microphone record checkbox for the ALSA MIXER on reboot.  Is there anyway to prevent this?  Also, is there any plans to support a record checkbox for the microphone in the Sound Indicator Applet 0.4.X?  

In Ubuntu the only way to set the microphone record (that I'm aware of) is via the ALSA Mixer any other ways via the "just click on the sound icon on the desktop" approach?

V$H.

---

### Post by vsh3r on 2010-11-02
(see attached screenshot)

---

### Post by mastablasta on 2010-11-02
Have you tried to open the terminal and then typing:
 
>  
```
 
sudo alsactl 0

``` 
The 0 refers to which sound card on your system you are saving. If you only have one than it is safe to assume the device is 0
.
 
After this change your mic setting. this should save it i believe.

---

### Post by vsh3r on 2010-11-02
For some reason this doesn't work on Ubuntu 10.10.

V$H.

---

