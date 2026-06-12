---
title: "Synaptic Package Manager is missing"
date: 2012-01-16
forum: General Help
---

### Post by fredmt on 2012-01-16
Synaptic Package Manager was working just fine until I installed KDE alongside Gnome. Now, when I go to bring it up, it does not come up.

Can someone offer a bit of advice?

Oh! I have the latest version of Ubuntu...

---

### Post by oldos2er on 2012-01-16
Try running it in a terminal, it may give a hint as to what the problem is.

---

### Post by bluexrider on 2012-01-16
> **fredmt said:**
> Synaptic Package Manager was working just fine until I installed KDE alongside Gnome. Now, when I go to bring it up, it does not come up.

Can someone offer a bit of advice?

Oh! I have the latest version of Ubuntu...

Try in terminal

```
gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
```

---

### Post by epic.mint on 2012-01-16
i have this same problem simply call it from terminal or the run dialog with
```
gksudo synaptic
```
(you might need to install gksudo/gksu)

---

### Post by bluexrider on 2012-01-17
> **epic.mint said:**
> i have this same problem simply call it from terminal or the run dialog with
```
gksudo synaptic
```(you might need to install gksudo/gksu)
Isn't that interesting....your command does not call synaptic for me. I have to use the previous posted.

---

### Post by epic.mint on 2012-01-17
i'm using what once was kubuntu 11.10 but is now more like frankensteins monster and that command work's for me but not starting it from the xfce menu

---

