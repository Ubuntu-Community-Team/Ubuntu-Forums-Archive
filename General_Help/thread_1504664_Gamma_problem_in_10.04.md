---
title: "Gamma problem in 10.04"
date: 2010-06-08
forum: General Help
---

### Post by Bobulous on 2010-06-08
After following the helpful monitor calibration guide at

[http://www.normankoren.com/makingfineprints1A.html](http://www.normankoren.com/makingfineprints1A.html)

I found my monitor required xgamma to hold a setting of 0.84.

This can be done with `xgamma -gamma 0.84` but typing that every time the desktop is booted gets tedious, so I added the gamma value to the xorg.conf file.

Now, for reasons beyond me, when I boot into GNOME the gamma is back to its pasty looking default, but bizarrely if I type `xgamma` it reports that gamma is set to 0.84. I then have to type `xgamma -gamma 0.84` to actually get the gamma to affect the monitor output.

Does anyone have any idea why xgamma is seemingly paying attention to the xorg.conf file, but then failing to take effect on the monitor until I run the command manually?

---

