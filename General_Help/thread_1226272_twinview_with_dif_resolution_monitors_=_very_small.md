---
title: "twinview with dif resolution monitors = very small letters?"
date: 2009-07-29
forum: General Help
---

### Post by guidin360 on 2009-07-29
Hi all.. i'm new on this and this is the only thing to fix until i finish migrating from win****.
When i use only 1 single monitor it's fine, i have a DELL E198WFP and a LG HD 32" (1360x768)
The issue starts here:
I start nvidia-settings, and i configure to clone my lg to the dell, but, when i do it.. i have 2 probs
one is that in the lg i don't see the entire screen, i mean it's seems that is cutted off, for example i don't see the XFCE bar, or the right of the firefox, etc.
And the other.. is explained in the screenshot, see how horrible looks the xfce bar, firefox toolbar letters looks.

thx and sorry about my enligsh

---

### Post by CatKiller on 2009-07-29
Perhaps the monitors are running at different resolutions, and so the clone doesn't work properly? I've never used it.

Your text problem looks like the DPI setting is wrong. Perhaps X isn't being given (or is miscalculating) the correct DPI value. You might be able to fix it by setting the value in System &#8594; Preferences &#8594; Appearance &#8594; Fonts &#8594; Details, or by setting the DisplaySize value in the Monitor section of your xorg.conf.

---

