---
title: "need zip of hicolor icon theme for jaunty"
date: 2009-08-18
forum: General Help
---

### Post by nortexoid on 2009-08-18
I thought I would free up a little space by removing some icon themes I thought I never used, like hicolor. So as root I deleted the /usr/share/icons/hicolor directory. Big mistake. I now get all sorts of errors including "The NetworkManager Applet could not find some required resources. It cannot continue" when I run nm-applet (the network manager applet). Clicking "ok" causes the network to be disabled.

When I try to reinstall hicolor-icon-theme it installs only the folders in /usr/share/icons/hicolor with no icon image files. Odd. Likewise when installing the .deb.

Can someone zip up their /usr/share/icons/hicolor directory (pref for Jaunty?) and email it to me at [email]niburu1@hotmail.com[/email]. I would be forever in your debt.

---

### Post by Katalog on 2009-08-18
Have you tried booting from the live CD and copying the icons from the directory on the CD to your hard drive? It may complain that you don't have permission to mount your hard drive while your in live CD mode, but if it does just open up the terminal and type "gksu nautilus" and it will open nautilus in su mode and you can mount/copy anything you want.

FWIW, sorry to hear that you found out too late that a lot of programs and icon themes depend on hicolor.

---

### Post by nortexoid on 2009-08-18
A kind soul has solved my worries. Thanks!

---

### Post by HiImTye on 2009-08-18
rename them from .zip to .rar

if you don't have rar installed then

```
sudo apt-get install rar
```

the package manager should be able to open them then

---

