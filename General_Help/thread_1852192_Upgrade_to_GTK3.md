---
title: "Upgrade to GTK3?"
date: 2011-09-29
forum: General Help
---

### Post by galacticaboy on 2011-09-29
I have Ubuntu 11.04 and was wondering how I can upgrade to GTK3? Would it harm my system? How can I upgrade?

---

### Post by galacticaboy on 2011-10-02
***bump***

---

### Post by galacticaboy on 2011-10-03
***BUMP, yet again***

---

### Post by dniMretsaM on 2011-10-03
By Gtk3 do you mean GNOME3 + gnome-shell, GNOME3 + Unity, or just installing Gtk3? As for harming your system, that's pretty much impossible to predict. Some people have great success, some people
s system breaks. Just be sure you have your data backed up (or an image of your hard drive) and be open to the fact that you may have to re-install.

---

### Post by galacticaboy on 2011-10-03
> **dniMretsaM said:**
> By Gtk3 do you mean GNOME3 + gnome-shell, GNOME3 + Unity, or just installing Gtk3?

Just intalling GTK3

---

### Post by dniMretsaM on 2011-10-03
I think all you have to do is install the[FONT=Courier New] libgtk-3-0[/FONT] package. Search for in in the Software Center or run these commands in Terminal:
```
sudo apt-get update
sudo apt-get install libgtk-3-0
```

---

### Post by galacticaboy on 2011-10-03
> **dniMretsaM said:**
> I think all you have to do is install the[FONT=Courier New] libgtk-3-0[/FONT] package. Search for in in the Software Center or run these commands in Terminal:
```
sudo apt-get update
sudo apt-get install libgtk-3-0
```

Could doing this break my system?

---

### Post by dniMretsaM on 2011-10-03
I doubt it. I actually have it installed on my Kubuntu installation because apparently that GIMP 3.7.x requires it. Also, this is just adding the supporting libraries for Gtk3 applications, not actually installing a new desktop environment (like GNOME3 + Gnome-Shell). However, like I said a few posts ago
[QUOTE=dniMretsaM]...Just be sure you have your data backed up (or an image of your hard  drive)...[/QUOTE]

Again, since this is just installing the support libraries, the likelihood of it actually causing any major problems are extremely small (pretty much it's not going to bother anything at all). You might actually have it already installed and not know it like me.

---

