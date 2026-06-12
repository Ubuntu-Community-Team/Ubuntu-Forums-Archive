---
title: "Dark Screen - last question"
date: 2011-12-26
forum: General Help
---

### Post by EpicWorld on 2011-12-26
after i tried lots of things i think i finally find a sollution

```
sudo setcpi -s 00:02.0 F4.B=01
```
[LEFT]^that code just disambled that <snip> black screen, everything is great, but whenever i open a game or o restart the computer it turns again black to i need to type the code everytime. how to make it stay 4ever there?
[/LEFT]

---

### Post by Toz on 2012-01-01
To make it take effect whenever you start the computer, edit /etc/rc.local (from a terminal window):
```
gksudo gedit /etc/rc.local
```
...and insert _above_ the *exit 0* command, the following:
```
setcpi -s 00:02.0 F4.B=01
```
...and save the file (note, sudo is not required here since the file is run with root privileges on boot).

---

