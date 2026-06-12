---
title: "How to adjust brightness?"
date: 2011-07-31
forum: General Help
---

### Post by WubiAR on 2011-07-31
Hello,

I just recently installed Xubuntu 11.04 and I want to adjust the brightness levels. I tried using the corresponding buttons on my laptop, but they aren't working. Where can I find the brightness settings on the OS?

I tried this thread: [http://ubuntuforums.org/showthread.php?t=794362](http://ubuntuforums.org/showthread.php?t=794362) , but "Power Manager" didn't have that setting.

---

### Post by zero2xiii on 2011-08-06
It seems ubuntu does not yet support this.

There is a secondary option though. If you happen to have a Nvidia graphics card, install the drivers through (system . Administration > additional drivers) and then open up nvidia-settings, and then change the screen brightness there.

Other than that I couldn't get my screen to dim either (even in power manager, when I change the display brightness, nothing happens)

---

### Post by pasu11 on 2011-08-06
yup, as zero2xiii suggested, tweak the brightness in your video card driver. If you use Nvidia, you can go into nvidia-settings -> X Screen -> X Server Color Correction and you will see the Brightness tweaking area.

---

### Post by Toz on 2011-08-06
Another thing to try, if it is an nvidia card, add the following:
```
"Option "RegistryDwords" "EnableBrightnessControl=1"
``` to the device section in your /etc/X11/xorg.conf file.

---

### Post by realzippy on 2011-08-06
Which laptop ?

---

