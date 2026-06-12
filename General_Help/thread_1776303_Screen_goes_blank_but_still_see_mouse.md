---
title: "Screen goes blank but still see mouse?"
date: 2011-06-05
forum: General Help
---

### Post by itz_speld_rong on 2011-06-05
[FONT=Arial][SIZE=2]     This is happening to multiple computers (friend's Mac running Ubuntu along with my laptop), both of which are typically maintained by myself. For some reason, the screen goes black after a certain idle time. I have [/SIZE][/FONT][FONT=Arial][SIZE=2]check the power management settings and the screen saver settings. It seems that everything on the screen goes black but the mouse is still visible (and feeling moving). The mouse also interacts with what is on the desktop (that I cannot actually see). I can click things and get responses, etc. The only way I've thought to get around the problem is by closing the laptop and then I get prompted to put in my password once it's re-opened, and everything is back to normal (desktop working fine).

This little bundle of fun makes watching videos rather unenjoyable and I've ran out of ideas. I've check around on this forum and google but haven't really found somebody with the same problems. It sounds like some setting that I've just over-looked in my lack of experience with Ubuntu. Any suggestions?


Thanks a lot guys. :)[/SIZE][/FONT]

---

### Post by Gauge0123 on 2011-07-16
I have the same exact same problem off and on with my laptop. I am running 11.04 (classic gnome) on a Toshiba Satellite. Any help would be greatly appreciated.

---

### Post by wojox on 2011-07-16
It really helps if you post more info like video drivers:

```
lspci | grep VGA
```

:D

---

### Post by Gauge0123 on 2011-07-17
@wojox

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

### Post by Gauge0123 on 2011-08-02
Bump

---

### Post by gpaciga on 2011-12-01
I am having this problem as well. I am using an HP pavillion dv4 laptop with an Acer monitor plugged in. After 10 minutes idle the screen goes black, and when I try to bring it back I only see the mouse on both monitors. It is quite odd that the mouse behaves as normal, changing between an arrow, hand, and text input depending on what it thinks it's hovering over, even though there's nothing but black. 


$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

For now I've just changed the settings to never turn off the screen.

I just recently upgraded to 11.10 but for the first few days this didn't happen. It's only been in the last two days this has started.

---

