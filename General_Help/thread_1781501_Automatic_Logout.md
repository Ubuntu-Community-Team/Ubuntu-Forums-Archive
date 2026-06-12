---
title: "Automatic Logout"
date: 2011-06-13
forum: General Help
---

### Post by gameoutcast2 on 2011-06-13
sometimes when i log in at startup it will automatically log me out. this can happen two or three times before i can get on. does anyone have a solution.

---

### Post by kandisa on 2011-06-14
I am also facing same problem :(
Any Help ????

---

### Post by zeroseven0183 on 2012-01-07
What version of Ubuntu are you using? I am also trying to figure out the cause of this problem, looking into some bug reports in Launchpad.

My Ubuntu is set to automatically login on startup. I noticed that often times right after startup when I started typing or opening an application (either a browser, file manager, or any) it accidentally logs out to the default login screen. A black screen with some garbled texts appears before it.

The problem is either with gdm or Xorg or in my case, LightDM, I think. I'm using 64-bit by the way.

---

### Post by zeroseven0183 on 2012-01-07
I found this [bug report #892485]("https://bugs.launchpad.net/lightdm/+bug/892485") that describes exactly what happen during autologin. Anyone else having the same problem?

---

