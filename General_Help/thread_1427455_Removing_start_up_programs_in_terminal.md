---
title: "Removing start up programs in terminal"
date: 2010-03-11
forum: General Help
---

### Post by kyletstrand on 2010-03-11
I recently learned how to add start up programs in the terminal using the following command:

```
ln /usr/bin/whateverprogram ~/.kde/Autostart
```

This worked, but now I want to remove some start up programs using the command line.  Can someone point me in the right direction to what I need to do for this?

I'm assuming that default start up programs are not links in the ~/.kde/Autostart folder because when I run:

```
ls -a ~/.kde/Autostart
```

I only find the files that I have set to start up.

Any help would be appreciated!

---

### Post by geirha on 2010-03-11
In Gnome, the default startup programs are controlled by .desktop-files in /etc/xdg/autostart/

To disable one, you copy it to ~/.config/autostart/, edit it in a regular text editor and change
```
X-GNOME-Autostart-enabled=true
```
to
```
X-GNOME-Autostart-enabled=false
```

Might be similar in KDE, but I don't have much experience with KDE.

---

### Post by Daveski on 2010-03-11
> **kyletstrand said:**
> 
I'm assuming that default start up programs are not links in the ~/.kde/Autostart folder because when I run:

```
ls -a ~/.kde/Autostart
```

I only find the files that I have set to start up.

Any help would be appreciated!

You have created hard links - so the ls command shows essentially a 'copy' of the file you linked into the Autostart directory. You may safely delete these and check that the original file in the original location still exists, but the link in the Autostart has been removed:
[URL="http://en.wikipedia.org/wiki/Ln_(Unix)"]
http://en.wikipedia.org/wiki/Ln_(Unix)[/URL]

---

### Post by GameManK on 2010-03-22
What sort of programs are you trying to remove from starting up?

Many services on your system are started before you log in by init.  Some programs use .config/autostart, similar to .kde/Autostart.  KDE also restores all your programs from the last session.  Those are in .kde/share/config/session

---

