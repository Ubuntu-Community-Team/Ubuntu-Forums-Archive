---
title: "No Sound on Realtek ALC888"
date: 2011-10-30
forum: General Help
---

### Post by theoretical on 2011-10-30
I have a Dell Inspiron 530 with integrated sound. It worked perfectly in Windows, but sound refuses to work in Linux. I installed the drivers on Realtek's site already (both versions, neither work). Is there anything I can do to get sound to work?

---

### Post by Rodney9 on 2011-10-30
Have a look here - [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by theoretical on 2011-10-30
Thanks. When I view the report, I saw that there was no version number displayed for Driver: . I tried reinstalling the driver from the alsa site, but it just gives me errors even though I followed the instructions on how to install it to the letter.

Here's my report: [http://www.alsa-project.org/db/?f=2fde98fe1bf3a361606ce32591e4892c09941175](http://www.alsa-project.org/db/?f=2fde98fe1bf3a361606ce32591e4892c09941175)

---

### Post by theoretical on 2011-11-01
My issue is still not resolved! Apparently I'm missing the Alsa driver and typing in alsamixer in Terminal doesn't do anything. It just says Unable to locate package. Is there a repository where I can just get everything quickly and easily?

---

### Post by Steve R. on 2011-11-01
See if you can install the GNOME ASLA Mixer from the Synaptic Program Manager. Under the "*CA016*" tab make sure that nothing is checked. 

In my case, everything looked OK in Ubuntu, but when I downloaded GNOME ASLA Mixer and installed it, "*digital*' was checked.  After unchecking the sound came on. 

I don't have a Dell so it may or may not work for you.

---

### Post by theoretical on 2011-11-01
> **Steve R. said:**
> See if you can install the GNOME ASLA Mixer from the Synaptic Program Manager. Under the "*CA016*" tab make sure that nothing is checked. 

In my case, everything looked OK in Ubuntu, but when I downloaded GNOME ASLA Mixer and installed it, "*digital*' was checked.  After unchecking the sound came on. 

I don't have a Dell so it may or may not work for you.
I don't see where the CA016 is. Could you please direct me to it? Thanks.

---

### Post by Steve R. on 2011-11-02
See the attached screen image.

---

