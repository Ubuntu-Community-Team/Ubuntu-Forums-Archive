---
title: "Is there anything in Unity that is part of the core of the distro?"
date: 2012-02-07
forum: General Help
---

### Post by nolag on 2012-02-07
I am installing GNOME 3 shell as I type, I hate unity so I want to uninstall it, but I just want to make sure there is nothing intermingled with the OS.  Ideally there should not be, the DE should not be tied into the OS, but sometimes odd things happen, so I just want to be sure.

Thanks in advance for any help.

---

### Post by wolfen69 on 2012-02-08
You are better off leaving it. More bad can happen by removing it than leaving it. Unity will be invisible while using gnome 3, and doesn't take up much room.

---

### Post by satanselbow on 2012-02-08
Unity can be removed through synaptic / USC no problem and no ill effect - the day that changes Ubuntu will sink like an opensource stone.

---

### Post by 3rdalbum on 2012-02-08
> **satanselbow said:**
> Unity and its related evil can be removed through synaptic / USC no problem and no ill effect

Describing it as "evil" is a bit childish, and very insulting to its developers.

There's really no need to remove Unity altogether, it doesn't use much space. On a more practical note, Brasero and a few other programs in Ubuntu are linked against libunity to allow them to interact with the Launcher API, so you can't safely remove the libunity package.

Also you should make sure you have some sort of 2D session available; either Gnome Session Fallback (Gnome Classic) or Unity 2D, or a plain window manager like Openbox. Otherwise, if you ever have a problem with graphics drivers or have to install a totally different graphics card, you won't be able to get to a desktop without a 2D session.

---

### Post by EbnorEqvine on 2012-02-12
OP has probably already figured something out, but for whoever comes along with the same question, I suggest installing an alternative DE before uninstalling Unity. You'll see if you try to uninstall Unity with USC that gnome session manager has to go as well, so it would be unwise to uninstall Unity without a backup session manager.

---

