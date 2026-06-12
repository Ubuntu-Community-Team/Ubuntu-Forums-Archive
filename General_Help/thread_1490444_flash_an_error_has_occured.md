---
title: "flash: an error has occured"
date: 2010-05-22
forum: General Help
---

### Post by viralmeme on 2010-05-22
I'm using Lubuntu, I keep getting this error on FF and Chrome, any solutions ?

`an error has occured, please try again later'

---

### Post by phillw on 2010-05-23
Hi,

I've been having a bit of 'fun' with flash and chromium of late. I'm not in my lubuntu machine at the moment, but have gotten it working happily following these instructions [http://www.ubuntugeek.com/howto-enable-flash-support-for-google-chromium-browser.html](http://www.ubuntugeek.com/howto-enable-flash-support-for-google-chromium-browser.html) That will put the flash on so FFox can use it and copy it over for Chromium.

If you get no joy with that, then try ```
sudo update-java-alternatives --set java-6-sun
``` 

After either (or both) of the above, you need to restart Chromium / Ffox.

Regards,

Phill.

---

### Post by viralmeme on 2010-05-24
Fixed, thanks, I wonder what caused it, just started to get random flash crashes.

---

