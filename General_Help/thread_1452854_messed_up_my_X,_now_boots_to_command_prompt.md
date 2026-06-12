---
title: "messed up my X, now boots to command prompt"
date: 2010-04-12
forum: General Help
---

### Post by Dragonbite on 2010-04-12
I have a small (12") laptop screen (4:3 ratio) and I connected my system to an (undetected, Spectre) widescreen monitor.  I tried changing the resolution of the widescreen monitor when a pop-up message (something about virtual settings?) popped up.  

I foolishly clicked "OK" and it told me I have to restart to take effect.  

When I restarted, I would get the loading-up splash screen but instead of the login prompt I find myself in a CLI and "start x" doesn't work.

How can I reset my X back to what it was before, or have the system scan and reset it? Could I just delete the .config file (and if so, where is it)?

---

### Post by wojox on 2010-04-12
You could reset it:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Dragonbite on 2010-04-12
That didn't do anything.

There was no feedback when I ran it, if that makes any difference.

---

### Post by nothingspecial on 2010-04-12
If you boot into recovery mode, isn`t there an option to fix X (or whatever they call it atm)

---

### Post by 98cwitr on 2010-04-12
sudo apt-get remove ubuntu-desktop
sudo apt-get purge ubuntu-desktop
sudo apt-get install ubuntu-desktop

---

### Post by wojox on 2010-04-12
I guess you try moving it:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

What are you using for a Graphics card/chip?

---

### Post by Dragonbite on 2010-04-12
> **nothingspecial said:**
> If you boot into recovery mode, isn`t there an option to fix X (or whatever they call it atm)

I set my timeout=0, so getting into grub is not easy and since it's Grub2 I am still trying to find the menu.lst equivalent.

> **98cwitr said:**
> sudo apt-get remove ubuntu-desktop
sudo apt-get purge ubuntu-desktop
sudo apt-get install ubuntu-desktop
 That seems a bit extreme, dontcha think ;)

> **wojox said:**
> I guess you try moving it:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

What are you using for a Graphics card/chip?
I'm using Intel.

That seemed to do it though.  Thanks!

---

### Post by 98cwitr on 2010-04-12
sure fix though ;)

---

