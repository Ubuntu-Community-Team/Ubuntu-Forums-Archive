---
title: "Video driver problem: HDRadeon 3300 Integrated"
date: 2010-10-20
forum: General Help
---

### Post by mp29k on 2010-10-20
Yesterday, my Ubuntu 10.10 install broke out of nowhere.

On startup, fairly regularly I get scrambled screen in various degrees (usually static looking scramble on the bottom 50% of the screen, black on the top half) when trying to open the GUI.

This requires a power button reboot.  Nothing I have done seems to solve it.  I tried to install the proprietary driver from AMD/ATI, but this made performance suffer significantly.  I aggressively removed this driver, and re-installed the default.  

No amount of change made to Compiz (including turning effects completely off) has an impact.

I found this error in my boot log:

"fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver"

Can someone help me to understand whether this is resulting in my errors, and what I can do to fix it?

Thanks, -K

---

