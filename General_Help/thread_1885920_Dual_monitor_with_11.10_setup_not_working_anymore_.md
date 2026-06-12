---
title: "Dual monitor with 11.10 setup not working anymore - please help!!"
date: 2011-11-24
forum: General Help
---

### Post by nimonika on 2011-11-24
I did  a packgae manager update yesterday and it turns out that my dual monitor setup has stopped working. I have poor vision so I really need to connect to a much bigger screen, but since yesterday, when I connect the screen to my laptop, the screen does not automatically reset itself to the laptop display. Even after lots of trial and error with the display settings, I am getting different dispalys on the laptop and external screen and right now only the big screen is active while the laptop has blanked out.

Please can someone help em setup my dual screens for 11.10 properly.

Many thanks

Monika

---

### Post by raja.genupula on 2011-11-24
what kind of video drivers you're using ?

---

### Post by nimonika on 2011-11-24
> **raja.genupula said:**
> what kind of video drivers you're using ?


00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])

---

### Post by raja.genupula on 2011-11-24
```
sudo  dpkg-reconfigure xserver-xorg
```

try this

---

