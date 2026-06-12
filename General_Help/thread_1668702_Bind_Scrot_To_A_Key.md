---
title: "Bind Scrot To A Key"
date: 2011-01-16
forum: General Help
---

### Post by Hur Dur on 2011-01-16
So, I want to bind the terminal command "scrot -q 85 screenshot.jpg" to the key PrtSc. How do I do this? I am using Arch Linux, and IceWM. I tried editing the icewm keys file, and add the binding there, but it did not work.

---

### Post by VCoolio on 2011-01-16
Why not ask in archlinux forums? Anyway, pacman -S xbindkeys and create a config file by xbindkeys -d > ~/.xbindkeysrc, then add two lines:
```

"scrot -q 85 screenshot.jpg"
   Print
```

---

### Post by Hur Dur on 2011-01-16
> **VCoolio said:**
> Why not ask in archlinux forums? Anyway, pacman -S xbindkeys and create a config file by xbindkeys -d > ~/.xbindkeysrc, then add two lines:
```

"scrot -q 85 screenshot.jpg"
   Print
```

Arch seems more of a RTFM community, and I thought I would be more likely to get help here. Thanks for the mini guide. I will try when I get back on my computer.

---

### Post by Hur Dur on 2011-01-16
It worked. Thank you, my good man.

---

