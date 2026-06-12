---
title: "Visual Effects - Acer Aspire One 751h"
date: 2010-08-04
forum: General Help
---

### Post by Twizlerr on 2010-08-04
Okay so when I got to **System>Preferences>Appearance>Visual Effects** I have the option to chose what I want (in other words, nothing is grayed out). Though, if I chose anything other than "No effects" the screen does some weird stuff. It goes black, then back to normal, black again, logs me out, looks like it is rebooting, and then brings me to the login screen. That's not *exactly* what happens, but it pretty much summarizes it.

I decided to run the Compiz-check and these are my results:
```
 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
 Driver in use:         Unknown
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [SKIP]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: Unknown driver in use. 

Would you like to know more? (Y/n) y

 Your driver is not widely known to work with Compiz and thus may be
 blacklisted on certain distributions.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N)
```I didn't skip the blacklist check because I don't want to risk encountering any problems again.

So, I see it says it hasn't identified a driver. What's the problem, and how can I fix it?

Thanks in advance

Acer Aspire One (751h model)
Ubuntu 10.04 / XP dual boot

---

### Post by ajgreeny on 2010-08-04
I think it's a known problem of the poulsbo graphics controller and ubuntu/UNR, but I will have to leave you to search a bit more, though [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) looks useful.

---

### Post by Twizlerr on 2010-08-04
> **ajgreeny said:**
> I think it's a known problem of the poulsbo graphics controller and ubuntu/UNR, but I will have to leave you to search a bit more, though [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) looks useful.

Unfortunenately, I have already followed that web page's instructions so I could get the correct resolution, and it doesn't fix this problem :/
I guess I just have to live with no effects (and no Docky! :() until a fix is released...
Thanks for your response though

---

### Post by snowpine on 2010-08-04
Here is some interesting reading material on the Intel GMA500 Poulsbo drivers: [http://www.linux.com/news/hardware/desktops/166625-blaming-intel-for-how-the-world-is](http://www.linux.com/news/hardware/desktops/166625-blaming-intel-for-how-the-world-is)

---

