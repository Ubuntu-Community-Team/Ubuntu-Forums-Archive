---
title: "ati mobility radeon HD 5650 driver strange display issue"
date: 2011-02-18
forum: General Help
---

### Post by RafikiSanchez on 2011-02-18
Hi, Putting this in general, but it might belong somewhere else, sorry. Just got a new laptop, installed 10.10 64. As soon as I got it, as I expected, I was prompted to install the amd/ati proprietary video driver. When I did, I was able to turn on the extra visual effects and they worked fine.

What was strange was that instead of the smooth desktop layout that I had right before the install, a lot of the display became .. blocky, like the old windows 2000 battleship gray with solid black lines as borders and no rounded corners.. etc. This didn't happen everywhere, just in the system boxes (alerts, utilities etc) and in the area between desktop window title bars and the contents of the window itself (like the menus and toolbars). Also in the main panel (with the system tray, applications, places, etc).

When I removed the driver, the display went back to normal, and for now its much easier on the eyes, but I would really like to use this 5650 graphics driver .. anyone seen anything like this before?

Thanks.

EDIT: here's a before and after..

[nowhere.divsharp.com]("http://nowhere.divsharp.com")

EDIT: it seems like the appearance settings aren't being applied universally, and some parts of the display are falling back to defaults.. I know next to nothing about this, so any help is appreciated.

---

### Post by RafikiSanchez on 2011-02-18
bump? :(

---

### Post by RafikiSanchez on 2011-02-19
So, I still don't know what caused the problem, or what the real fix is.. but I solved it, though not elegantly. After some digging, I found out the preinstalled themes for 10.10 are in

/usr/share/themes

And once I read the gtkrc files for each, I found one in theme "Raleigh" which said that it was the theme that the system falls back to if no other theme is selected. I just copied the theme files from "Radiance" into that dir and after a reboot, finally, nice looking theme.

I can't figure out still why that "Raleigh" was being used at all, especially because the windows borders for "Radiance" were displaying fine the whole time. If anyone knows how this could have happened, I would definitely appreciate the answer.

Also, if anyone knows a more elegant way to fix this, I'm all ears.

(copy of answer from my more [relevant thread]("http://ubuntuforums.org/showthread.php?t=1691106") regarding this topic)

---

