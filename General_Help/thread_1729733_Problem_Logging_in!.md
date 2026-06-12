---
title: "Problem Logging in!"
date: 2011-04-15
forum: General Help
---

### Post by linuxmaniack on 2011-04-15
Yesterday, i rebooted my pc, and when logging in, it automaticly logs out again. I have installed the KDE desktop, unity, LXDE, and xfce, and they dont work! Anyway heres what happens: 

The screen goes blank for 1/2 of a second, and then it goes back to the login screen. This is so anoying as i use ubuntu for games, internet ect. Anyone else had this problem? I dont really want to reinstalling it, but is there a command that will work like there is always with ubuntu? Thanks!

---

### Post by techunit on 2011-04-15
You might try dropping to the terminal and logging in to see if there are problems with processes. Who knows not all WM and DEs interface correctly together.

Good Luck.

PS. To drop to a terminal hit ctrl-alt-f1

---

### Post by tredegar on 2011-04-15
Login to a text-only terminal:
**<CTRL><ALT><F2>**
Login as yourself.
Check your disk space **df -h** (you should have approx. >10% free)
Try starting X with **startx**
See what happens, you will be able to read the error messages.

---

### Post by linuxmaniack on 2011-05-15
Sorry i havent replyed in ages, but thanks that worked!

---

