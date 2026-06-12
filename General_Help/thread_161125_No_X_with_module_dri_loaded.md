---
title: "No X with module dri loaded"
date: 2006-04-16
forum: General Help
---

### Post by rohrbold on 2006-04-16
Whenever I install a new version of Ubuntu (Breezy or Dapper), the dri module freezes the whole system in a way that I neither can log into an X session nor am I able to switch to one of the framebuffer consoles. So after each installation I have to boot in recovery mode or from another Linux installation and edit the xorg.conf file (comment the "Load dri" line).
I have an Acer Travelmate 803 laptop with an ATI Mobility Radeon 9000 video card:
```
martin@bart:~$ lspci -X | grep VGA
PCI:1:0:0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000]
```

This is a bit annoying and took me some time to find the solution. Even worse I couldn't figure out how to use 3D acceleration or use the proprietary ATI fglrx driver to get better X performance.
Can anybody help me on this issue?

---

