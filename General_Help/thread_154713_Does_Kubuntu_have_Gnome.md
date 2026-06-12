---
title: "Does Kubuntu have Gnome?"
date: 2006-04-03
forum: General Help
---

### Post by jacatone on 2006-04-03
I got a copy of the new Kubuntu 5.10 which obviously comes with KDE. Does it also have Gnome as well. If so, how would I install it? Thanks.

---

### Post by rado_london on 2006-04-03
Kubuntu doesnt have it on the cd. If you have internet connection type the following line into the terminal:
```
sudo apt-get install ubuntu-desktop
```

You will end up with gnome which you can choose from GDM/KDM.

Good luck

---

### Post by gingermark on 2006-04-03
If you type "sudo apt-get install ubuntu-desktop" you will get all the ubuntu packages, including gnome.

Or you can just install gnome, have a look in Adept for the various packages.

If you prefer to use ubuntu, you could just install a base system then apt-get install ubuntu-desktop - that would give you just ubuntu.

---

### Post by jacatone on 2006-04-04
What is Adept? Will installing Gnome give me it's file manager and so on or will it still be KDE? Thanks.

---

### Post by Barrakketh on 2006-04-04
[QUOTE=jacatone]What is Adept? Will installing Gnome give me it's file manager and so on or will it still be KDE? Thanks.[/QUOTE]
Adept is Kubuntu's package manager.

Installing ubuntu-desktop will install everything that would've been installed had you just used the Ubuntu install CD.  That includes Nautilus.

---

