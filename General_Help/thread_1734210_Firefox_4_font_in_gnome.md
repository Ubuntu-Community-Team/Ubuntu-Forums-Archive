---
title: "Firefox 4 font in gnome"
date: 2011-04-20
forum: General Help
---

### Post by cloroxmartini on 2011-04-20
So I know this is a minor nuance and it doesn't effect usability at all but it still bugs me. I was using gnome on Ubuntu and decided to install KDE. KDE didn't work properly and so I uninstalled it. But now Firefox still has the KDE font and I can't figure out for the life of me how to change it back. I've had this problem before on another computer and I can't remember if I fixed it on there or not. Any help would be appreciated.

---

### Post by mike555 on 2011-04-20
in Firefox can't you set the fonts you want it to use? Edit>preferences>Content>fonts&colors-advanced.

---

### Post by cloroxmartini on 2011-04-20
Yes, I messed around with that. But it seems like Firefox isn't conforming to the system font setting like it did before I installed KDE. Especially when right clicking inside Firefox as opposed to right clicking in another windows or on the desktop. The fonts in the firefox menus are different.

---

### Post by Copper Bezel on 2011-04-20
Oh, I fought with this for ages! Install the package qt4-qtconfig. It'll show up in your Preferences menu or can be launched with qtconfig. It's the only reliable way I've found to configure Qt settings under Gnome with KDE installed alongside.

You can set up proper subpixel smoothing for Qt fonts, which will fix Firefox, and as a bonus, conform your Qt apps' widgets to your GTK+ styling.

---

### Post by cloroxmartini on 2011-04-23
I downloaded qtconfig and messed around with it but still couldn't get it to change.

---

### Post by lovinglinux on 2011-04-23
Try this: [http://ubuntuforums.org/showthread.php?t=1556849](http://ubuntuforums.org/showthread.php?t=1556849)

---

### Post by cloroxmartini on 2011-04-24
That worked. Thanks a lot.

---

### Post by lovinglinux on 2011-04-25
> **cloroxmartini said:**
> That worked. Thanks a lot.

You are welcome.

---

