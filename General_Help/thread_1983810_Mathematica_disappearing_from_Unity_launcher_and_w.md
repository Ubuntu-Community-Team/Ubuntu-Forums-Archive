---
title: "Mathematica disappearing from Unity launcher and window navigation broken"
date: 2012-05-20
forum: General Help
---

### Post by Ingenium on 2012-05-20
After upgrading to 12.04 (from 11.04 with Gnome classic), I have trouble using Mathematica 8. When I run it, the icon appears briefly in the Unity launcher with my other open apps, then it disappears. Window navigation for Mathematica is then broken (I can't even alt-tab, it's simply not even in the list. The only way to get back to the window if it's in the background is Super+W and select it there). Sometimes if I close it and the Mathematica Welcome screen appears, the launcher icon will return and I can proceed from there OK, but this is still hit and miss. The last 10+ times I've launched it this hasn't worked.

What would cause a program to behave like this? Mathematica is the only program that does this for me. Could it be something Java related?

EDIT: I think I may have found a workaround. If I run it with -nosplash, it seems to work. So it's something with the splash screen that is likely causing it.

---

### Post by rajarshihri on 2012-05-23
I have the similar problem. When I launch mathematica, its window opens, but as soon as you use alt+tab to see other windows (for example terminal window) and try to switch back to mathematica window, it does not show in the windows list.

However if you manually minimise the other windows, you see the mathematica window in the back. But you can't get it in the windows list while using alt+tab.

rajarshi

---

### Post by tom67 on 2012-05-31
> **Ingenium said:**
> 
EDIT: If I run it with -nosplash, it seems to work.

Thank you Ingenium, it really works. 
It helped not only my work but also my long-term effort to attract colleagues to ubuntu :)

---

