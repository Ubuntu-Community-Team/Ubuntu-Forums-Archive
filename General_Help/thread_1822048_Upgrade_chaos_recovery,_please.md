---
title: "Upgrade chaos recovery, please"
date: 2011-08-10
forum: General Help
---

### Post by oldarney on 2011-08-10
My last update killed my 3D acceleration and Unity. While trying to fix it, all the fonts and images went UPSIDE DOWN. Right now I'm on safemode.

How do I recover?

Asus UL30A, intel i8042, GMA 4500MHD
Ubuntu 11.04

---

### Post by raja.genupula on 2011-08-10
do you have any previous kernels in your grub menu , if so boot from there

---

### Post by Mark Phelps on 2011-08-10
Detailed instructions:

1) Hold down a SHIFT key while booting.  This should display a GRUB menu
2) You may see an entry their for Older ubuntu versions.  If so, choose that.
3) Select one of the older kernel versions, the Recovery Mode option.
4) When offered, choose the Repair Broken packages option.
5) If that completes successfully, then choose the Normal Boot option
6) If that does not get you into a desktop, enter "startx" from a command line.

---

### Post by oldarney on 2011-08-10
**[COLOR=Purple]THANK YOU! [/COLOR]**
I won't have to restart my life, but won't be updating for a while. I'm a CS major and I think I should get to know Linux much deeper, any books you'd recommend?

> **raja.genupula said:**
> do you have any previous kernels in your grub menu , if so boot from there

I tried that, but I didn't use recovery mode.

> **Mark Phelps said:**
> Detailed instructions:
6) If that does not get you into a desktop, enter "startx" from a command line.

That got me into a desktop without gnome-panel or unity, so I just restarted, and that worked.

---

### Post by raja.genupula on 2011-08-11
> **oldarney said:**
> **[COLOR=Purple]THANK YOU! [/COLOR]**
I won't have to restart my life, but won't be updating for a while. I'm a CS major and I think I should get to know Linux much deeper, any books you'd recommend?



  .
get linux bible , its have everything what ever you want

---

