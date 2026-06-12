---
title: "Losing power during update"
date: 2011-02-13
forum: General Help
---

### Post by a_p3rson on 2011-02-13
My friend is very new to ubuntu, and he made the horrible decision to update ubuntu while on battery power. Needless to say, he ran out of battery while updating. Now when he turns on, he appears to be stuck at loading GDM, all he can see it the bottom bar with only a shutdown button. Any help

---

### Post by An Sanct on 2011-02-13
If he can boot into safe mode (pressing 'e' during startup) or can acces the terminal (Ctrl + Alt + a function number from one to seven), then he can 
```
sudo apt-get update
```and then 
 ```
sudo apt-get upgrade
```Ctrl + Alt + F7 brings you back to the GUI

---

### Post by sikander3786 on 2011-02-13
Press Ctrl + Alt + F1 at your GDM screen and login to the tty1.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install -f
sudo dpkg --configure -a
```

Post the error messages if any.

---

### Post by An Sanct on 2011-02-13
And after that, 
```
sudo apt-get -f install
```
will fix broken packages, if any ...

---

### Post by a_p3rson on 2011-02-13
Also, is there any way to make an error message if someone tries to update/upgrade on battery power? I know that the installer for Ubuntu 10.10 didn't allow installation on battery power, how did it do that?

---

### Post by Quackers on 2011-02-13
I thought there was one. I've seen one somewhere, but in all honesty, I can't remember the exact circumstances.

---

