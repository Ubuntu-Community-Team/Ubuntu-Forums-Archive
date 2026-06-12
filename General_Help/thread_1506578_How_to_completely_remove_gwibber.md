---
title: "How to completely remove gwibber?"
date: 2010-06-10
forum: General Help
---

### Post by rudysuryanto on 2010-06-10
I have tried remove from ubuntu software center and Synaptic Package Manager, but when I reinstall Gwibber, it directly load from software list, and not download from internet. I want completely remove Gwibber, so if I want to reinstall Gwibber, my system download from internet and not install from database previous installation. How is to do it? Thank's.

---

### Post by Svens on 2010-06-10
```
sudo apt-get clean
``` should do the trick. :)
or maybe 
```
 sudo apt-get autoclean 
```
I forgot the difference. :D

---

### Post by scouser73 on 2010-06-10
Go to Terminal and copy & paste this command:**> sudo apt-get autoremove gwibber**

---

### Post by Svens on 2010-06-10
Grrr, autoremove.
Could somone explaing difference between clean, autoclean, remove, autoremove?

---

### Post by scouser73 on 2010-06-10
**sudo apt-get clean** & **sudo apt-get autoclean** are commands to clean up residual files after a program has been installed or removed.

**sudo apt-get remove** & **sudo apt-get autoremove** are the commands to remove a program from Ubuntu.

---

### Post by Svens on 2010-06-10
Thank you very much! Now it will be clear for me! :)

---

### Post by EJeanmaire on 2010-06-10
sudo apt-get purge gwibber

that is what you are looking for, that is the complete removal.

---

### Post by Soul-Sing on 2010-06-10
when removing apps via cli, you get additional information over residual files and how to remove them via the terminal.

---

