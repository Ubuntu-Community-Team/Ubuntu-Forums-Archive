---
title: "Parcellite stopped working"
date: 2010-10-12
forum: General Help
---

### Post by veggen on 2010-10-12
I've been using Parcellite since Jaunty and it used to work ok, but at some point (since Lucid I think) it stopped doing anything. It's still running (tried both regular and daemon mode) but it doesn't actually function. E.g. open Firefox, copy link location, close Firefox, clipboard content disappears.
Is Parcellite working for you?
Are there any alternatives (I don't need anything but clipboard protection, like Parcellite's daemon mode provides)?

---

### Post by veggen on 2010-10-12
Just tried glipper - doesn't even run. Tried clipboard-daemon, does nothing. What is wrong with recent Ubuntus that no clipboard manager will run?

---

### Post by sgosnell on 2010-10-12
Parcellite runs fine for me, I've never had any issues with it on Ubuntu from 8.04 onward, nor on Debian.  It just works.  There is almost certainly a configuration problem on your system, but I'm not sure where to start.  I assume parcellite is being started automatically at boot. Have you tried starting it manually?

---

### Post by Ron O on 2010-11-15
Same with me. Parcellite suddenly stopped working. Did a complete uninstall/reinstall. Uninstalled then and ran sudo apt-get build-dep parcellite. Then reinstalled. Nothing works. The icon is in the panel, but does not respond. Tried Glipper and got the same.

---

### Post by Ron O on 2010-11-15
Got Glipper working by right cliking a panel and using the "add to panel" then selecting clipboard manager. The confusion came because the app did not show up on any menu AND typing glipper in terminal gets you glipper: command not found.

Can't figure out the Parcellite thing though. But that's OK, Glipper seems to be very much the same.

---

### Post by Arcitens on 2010-11-17
> **Ron O said:**
> Same with me. Parcellite suddenly stopped working. Did a complete uninstall/reinstall. Uninstalled then and ran sudo apt-get build-dep parcellite. Then reinstalled. Nothing works. The icon is in the panel, but does not respond. Tried Glipper and got the same.

Same here. Parcellite just stopped working the other day for me. Don't think I've even had an updates recently so I'm not sure why it suddenly stopped working.

I might try Gilpper, but last I remember trying it it didn't work for me. If anyone has a solution or alternative, please post.

---

### Post by Ron O on 2010-11-17
I believe Parcellite has been abandoned. Try Glipper again- the new version is working pretty good for me, and it is an official gnome project, so it will probably survive system updates or be fixed if a conflict comes up. Simple as it is, the Help file is very useful for setting preferences and plugins.

I tried KDE's Klipper, then took it off. It starts a bunch of KDE libraries when you boot, and after your desktop comes up, you have to wait 15 seconds or more for it to finish loading up- EVERY time you start your system. Glipper does not do this.

---

### Post by Arcitens on 2010-11-18
I just switched to Pastie. Seems like it's working pretty well. People might try Glipper instead too as the above poster recommends. For Pastie, instructions from installing from PPA are here:

[http://www.omgubuntu.co.uk/2010/10/pastie-handy-clipboard-manager-indicator-applet/](http://www.omgubuntu.co.uk/2010/10/pastie-handy-clipboard-manager-indicator-applet/)

---

### Post by bingel on 2011-04-19
Solution could be removing all parcellite files (actions and history or maybe only history) located in user parcellite folder:

```
rm -fr ~/.local/share/parcellite/history
```

or

```
rm -fr ~/.local/share/parcellite/*
```


because these file could be corrupted.

---

### Post by monjope on 2011-06-13
> **bingel said:**
> Solution could be removing all parcellite files (actions and history or maybe only history) located in user parcellite folder:

```
rm -fr ~/.local/share/parcellite/history
```

or

```
rm -fr ~/.local/share/parcellite/*
```


because these file could be corrupted.

Thanks  =D>

---

### Post by Habitual on 2011-06-14
> **bingel said:**
> Solution could be removing all parcellite files (actions and history or maybe only history) located in user parcellite folder:

```
rm -fr ~/.local/share/parcellite/history
```

or

```
rm -fr ~/.local/share/parcellite/*
```


because these file could be corrupted.

**Especially** if you copied something in a spreadsheet! Oh boy. "How to break Parcellite."

Terminal:
```
killall -9 parcellite
rm -fr ~/.local/share/parcellite/history

```

and start it again, fixes it for me everytime. :)

---

