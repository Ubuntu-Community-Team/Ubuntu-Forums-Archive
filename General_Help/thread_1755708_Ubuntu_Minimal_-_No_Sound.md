---
title: "Ubuntu Minimal - No Sound"
date: 2011-05-11
forum: General Help
---

### Post by GreenDance on 2011-05-11
Hi, I've done a minimal ubuntu install, and just noticed I have no sound, if possible could someone tell me please what I need to do to have sound.

Thank You
GreenDance

---

### Post by GreenDance on 2011-05-12
Hi, I've installed xfce4-mixer, the sound was muted, i turned the sound up, but still no sound coming out my speakers :(. Please, if anyone can help I'll be most grateful. Thank You.

---

### Post by GreenDance on 2011-05-13
Hi, if I could ask again please, that would be great, this is to help my sister transfer from Windows to Ubuntu, without sound she's staying with Windows, please help, Thank You.

---

### Post by keithpeter on 2011-05-13
> **GreenDance said:**
> Hi, if I could ask again please, that would be great, this is to help my sister transfer from Windows to Ubuntu, without sound she's staying with Windows, please help, Thank You.

Hello

I'm no expert, but open a terminal and type 'alsamixer' at the prompt

You should see *something* like the attachment below. If you get 'command not recognised' or another error message, then you need to install alsa-utils

If you do see the alsa mixer display, and the 'bars' are all turned down and muted then you have to press tab to move to the next slider and m to unmute each one.

Cheers

---

### Post by GreenDance on 2011-05-13
Thank You, works.

---

