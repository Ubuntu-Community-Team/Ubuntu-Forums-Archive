---
title: "using xfce4, but want to remove exo-utils"
date: 2011-05-09
forum: General Help
---

### Post by grimslider75 on 2011-05-09
I need to remove exo-utils apperantly because i get an error every time I open a downloaded file using firefox which says, error: location is not a folder. 

what do I do?

---

### Post by kerry_s on 2011-05-09
install xdg-utils

---

### Post by grimslider75 on 2011-05-09
> **kerry_s said:**
> install xdg-utils
Already installed bud

---

### Post by kerry_s on 2011-05-09
> **grimslider75 said:**
> Already installed bud

I'd check the firefox setting, see what's set to open with.

---

### Post by Bazon on 2011-07-01
> **kerry_s said:**
> I'd check the firefox setting, see what's set to open with.

Did that, doesn't help. 
According to [this](http://ubuntuforums.org/showthread.php?t=1719689&highlight=exo-utils) and [that](http://askubuntu.com/questions/34260/why-do-i-get-a-the-location-is-not-a-folder-error-when-trying-to-open-files-usi) removing exo-utils is the solution, but when I try that, 39 other packets, including xubuntu-desktop and lots of xfce4 packets should be removed....
...how can I avoid that?

---

### Post by Bazon on 2011-07-01
OK, found the [solution](https://bugs.launchpad.net/exo/+bug/775640/comments/10):

> If you want to simply fix the opening of files but retain XFCE/exo you can simply open "exo-preferred-applications" and change the preferred "file manager" under "utilities" back to "Thunar"

I'm guessing the install of XFCE changes this default, anyway flipping it back to thunar certainly fixes the behaviour in Unity for me.

---

### Post by grimslider75 on 2011-11-21
Any way to keep xfce and nautilus at the same time? I prefer dolphin and nautilus to thunar since they both are capable of running in a split-window mode, unlike thunar. 

If there is no solution for this request, than I guess I can just live with the issue

---

