---
title: "Ubuntu Preferences font - letter &quot;e&quot; problem"
date: 2011-02-15
forum: General Help
---

### Post by jvtrain on 2011-02-15
Very new ubuntu/linux user.

Installed 10.10 and loving the learning and exploration of ubuntu. However, it seems I'm having issues with using the Ubuntu font in any appearance setting. Most other fonts seem to have no issue but when I use Ubuntu font for any appearance preference, the letter e is displaying mysteriously. If I italicize the Ubuntu font, it seems to go away, but remains with normal or bold settings. Screenshots attached. Any ideas/suggestions (other than the obvious "don't use Ubuntu font")? ;)

Screenshot.png = Ubuntu fonts
Screenshot-1.png = other fonts chosen

---

### Post by ahsan101 on 2011-02-15
> **jvtrain said:**
> Very new ubuntu/linux user.

Installed 10.10 and loving the learning and exploration of ubuntu. However, it seems I'm having issues with using the Ubuntu font in any appearance setting. Most other fonts seem to have no issue but when I use Ubuntu font for any appearance preference, the letter e is displaying mysteriously. If I italicize the Ubuntu font, it seems to go away, but remains with normal or bold settings. Screenshots attached. Any ideas/suggestions (other than the obvious "don't use Ubuntu font")? ;)

Screenshot.png = Ubuntu fonts
Screenshot-1.png = other fonts chosen
WEIRED!! I have had never heard of this...

---

### Post by Krytarik on 2011-02-15
Just try re-installing the respective font-package:
```
sudo apt-get install --reinstall ttf-ubuntu-font-family
```

---

### Post by jvtrain on 2011-02-15
Reinstalled the Ubuntu font before leaving for work today. Didn't seem to immediately remedy the issue but will check later today after a reboot. Issue seemed to occur after computer had gone to screensaver after booting.

---

### Post by jvtrain on 2011-02-15
So far so good on the Ubuntu font setup for windows, icons etc. Thanks for the tip.

---

### Post by jvtrain on 2011-02-17
Font corruption occurred again in the Ubuntu font... this time it was the d's. 2:1 odds next time around it's the poor c's. Reinstalled Ubuntu font family and back to normal after rebooting but a bit of odd to have to restart due to font issues often.

---

### Post by Krytarik on 2011-02-17
> **jvtrain said:**
> Font corruption occurred again in the Ubuntu font... this time it was the d's. 2:1 odds next time around it's the poor c's. Reinstalled Ubuntu font family and back to normal after rebooting but a bit of odd to have to restart due to font issues often.
It's a bit weird that it occurs repeatedly. However I believe a re-login would be sufficient.

---

