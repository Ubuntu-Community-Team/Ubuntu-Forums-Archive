---
title: "Undefined video mode number"
date: 2009-11-04
forum: General Help
---

### Post by MoscowModder on 2009-11-04
I am using Ubuntu 9.10 Netbook Remix installed with Wubi on Windows XP SP3.  The problem has been bothering me since before both the update from 9.04 and the installation of UNR.  When Ubuntu boots up, it tells me that I have an undefined video mode number (317 I think) and tells me to either type in one of the listed numbers or press space to skip.  How can I stop this annoyance?

---

### Post by soapBAR2 on 2009-11-04
Hi

Please post the output of 

> grep -v "#" /etc/X11/xorg.conf

---

### Post by MoscowModder on 2009-11-05
It told me to install a package, which I did.  Now it gives me this:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by MoscowModder on 2009-11-17
I would appreciate if someone could help me with this.  The problem still persists, and slows down my bootup by 30 seconds if I don't press the space bar.  While no more than an annoyance, it would be nice if I could fix it.

In other words, bump!

---

