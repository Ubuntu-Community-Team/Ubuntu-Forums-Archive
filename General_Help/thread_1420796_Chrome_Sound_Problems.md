---
title: "Chrome Sound Problems"
date: 2010-03-03
forum: General Help
---

### Post by Historyman on 2010-03-03
I know this is an issue, and I have most of the solutions found just by searching Google, but I can not seem to get flash sound to work in Google Chrome as downloaded by their website.  Firefox is fine, so I can survive using firefox. But i prefer chrome and would love to be able to do watch youtube and the like on chrome

I am running the 32x version .deb for ubuntu 9.10 on a Gateway MX7525 Laptop with an AMD64 Mobile Athlon processor if that helps

Thank You

---

### Post by Historyman on 2010-03-03
shameless bump

---

### Post by illuminaris on 2010-03-09
sudo cp /usr/lib/mozilla/plugins/flashplugin-alternative.so /opt/google/chrome/plugins/libflashplayer.so

This fixes it at least temporarily. I'm going to try it without the libflashplayer.so at th end to hopefully make it permanent

sudo cp /usr/lib/mozilla/plugins/flashplugin-alternative.so /opt/google/chrome/plugins/

---

### Post by Life On Mars on 2010-03-12
> **illuminaris said:**
> sudo cp /usr/lib/mozilla/plugins/flashplugin-alternative.so /opt/google/chrome/plugins/libflashplayer.so

This fixes it at least temporarily. I'm going to try it without the libflashplayer.so at th end to hopefully make it permanent

sudo cp /usr/lib/mozilla/plugins/flashplugin-alternative.so /opt/google/chrome/plugins/
Thanks for the tip :-)

Got my Chrome sound working again after I broke it.

---

