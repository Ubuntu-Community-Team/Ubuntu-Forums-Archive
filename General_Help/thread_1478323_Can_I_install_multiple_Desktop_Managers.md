---
title: "Can I install multiple Desktop Managers?"
date: 2010-05-09
forum: General Help
---

### Post by held7over on 2010-05-09
Ubuntu 10.04 Gnome

I have been looking for documentation on having several desktop managers installed, but haven't found it.

I noticed that at the login there is a drop down menu for Desktop Mangers. In addition to my Gnome desktop, can I install other desktop mangers such as icewm and select them at the login?

And when I select another desktop, will I experience a pick up in operating speed on lighter weight desktops or will I still be operating under GDM?

Thanks! :)

---

### Post by howefield on 2010-05-09
You can install pretty much as many Desktop Managers as you want, and select at login which you want to use.

If eg, you install kubuntu-desktop, you'll end up with "mixed" menus, when you log into Gnome, you'll still have KDE applications in the menu, and be able to use them and vice versa.

---

### Post by held7over on 2010-05-09
Thanks  howefield! That sounds pretty good.

So, I am assuming each desktop manager will select its own graphical manager when I select it as the desktop manager at the login? Is that correct? I will get the full speed increase on lighter weight desktops?

---

### Post by howefield on 2010-05-09
> **held7over said:**
> So, I am assuming each desktop manager will select its own graphical manager when I select it as the desktop manager at the login? Is that correct? I will get the full speed increase on lighter weight desktops?

That's correct.

---

### Post by nothingspecial on 2010-05-09
You do not have to install kubuntu-desktop (and all the kde stuff that goes with it)

```
sudo apt-get install kde-minimal
```

Also 

```
sudo apt-get install xfce4 openbox lxde
```

and others.

---

### Post by held7over on 2010-05-09
I did install kubuntu-desktop and it installed successfully, but when I logged into it, it was mud slow and the apps on the launch bar and on the desktop screen were not present, having red boxes with X's in them. I couldn't find the menu, either. I must have something messed up...or am missing some things....

I guess, for now, I will remove that, and try nothingspecial's approach of KDE minimal.

---

### Post by nothingspecial on 2010-05-09
It depends on your computer.

Kde takes a whole lot (depending on your perspective) of resources to run.

In "ubuntu land" there seems to be the consensus, that to try Xfce means you have to install xubuntu-desktop.

You don`t.

Same goes for kde.

You can install desktop environments (including Gnome, if you have started with something else) without installing a whole linux distribution.

---

