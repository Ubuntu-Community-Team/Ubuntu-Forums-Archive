---
title: "Uninstall in recovery mode?"
date: 2009-09-17
forum: General Help
---

### Post by qbert381 on 2009-09-17
Hey, I am fairy new to Ubuntu. I think I accidentally installed some wrong drivers for my video card. I know what they are (not the specific names but that they are ATI in brand name). Is it possible to unistall them from the system in recovery mode using one of the options that are available to me? I ask this because when I restarted my computer, the screen is all blurry and I am unable to do anything. Any help would appreciated. Thanks.

---

### Post by wojox on 2009-09-17
This will reset xorg.conf:

```
dpkg-reconfigure xserver-xorg
```

---

### Post by qbert381 on 2009-09-18
Thanks for the reply Wojox.
When I tried to enter:
"dpkg-reconfigure xserver-xorg"
It put me through a line of questioning, none of which had to do with my video card and I am still facing the same problem.
Essentially I need to uninstall drivers that I installed without going into the GUI, because everytime I do, the screen is all blurry and screwed up.
Is this possible?

---

