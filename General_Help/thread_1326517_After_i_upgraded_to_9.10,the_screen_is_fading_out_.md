---
title: "After i upgraded to 9.10,the screen is fading out to black after some minutes"
date: 2009-11-14
forum: General Help
---

### Post by TruebaseB on 2009-11-14
Hi,

After i upgraded my Ubuntu to 9.10,i noticed that after some minutes my screen is fading out to black,like i have a screensaver.

I checked the screensaver and it's disabled.
Also i have disabled the "turn of monitor after xx minutes" on the power management.

I searched on google for solution and i found a topic on this forum with the same problem.
A member says to put this in xorg.conf at the monitor section:

 ```
    Option           "BlankTime"     "0"
    Option           "StandbyTime"     "0"
    Option           "SuspendTime"     "0"
    Option           "OffTime"     "0"
```However i added those lines to my xorg.conf,i restarted the computer,but the problem remains unsolved.

It's very annoying,especially when i'm watching movies,because i must moving the mouse all the time.

Any idea guys?

**EDIT: Nevermind. :D**

---

