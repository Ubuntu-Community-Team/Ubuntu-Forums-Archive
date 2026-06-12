---
title: "Compiz"
date: 2012-05-16
forum: General Help
---

### Post by sen0140 on 2012-05-16
Hi, I was just wondering what Compiz actually does, I've read some threads saying that you can do some cool things with it and it says I have it installed under my synaptic package manager, but I can't find it anywhere when I wanted to use it.  Thanks for any help.

---

### Post by roelforg on 2012-05-16
It does the 3d effects and most of the other eye-candy on your desktop.

---

### Post by Zvlwab on 2012-05-16
Here's a quick list of compiz packages you may want to install:
compizconfig-settings-manager - GUI for configuring compiz, you are probably looking for this package.
compiz-fusion-plugins-main - Default compiz plugins.
compiz-fusion-plugins-extra - Extra plugins.
compiz-gnome - Used to use metacity as a window manager. Unless you want to use Emerald, you'll probably need this.
compiz - Metapackage containing some common compiz packages. You probably want to install this.

After installing the settings manager, you can run it by running```
ccsm
```

---

### Post by grahammechanical on 2012-05-16
This is Compiz

[http://www.compiz.org/]("http://www.compiz.org/")

It is both a compositing manager and a window manager. If you are using either Ubuntu 11.10 or 12.04 and you are logging in under Ubuntu (see menu under the cog icon at the log-in screen) then you will be using Compiz.

When we log-in under Ubuntu 2D we will be using Metacity as the compositing/window manager.

[http://en.wikipedia.org/wiki/Metacity]("http://en.wikipedia.org/wiki/Metacity")

We can make a few adjustments to the Unity user interface in System Settings>Appearance.

We can make more adjustments by installing CompizConfiguration Settings Manager (CCSM) and using the Ubuntu Unity Plugin.

We can also use CCSM to activate some special effects that Compiz will produce. Note the warning when CCSM loads.

Be prepared to log in to Ubuntu 2D to reverse your choices. Compiz effects will not work in Ubuntu 2D because the window/compositing manager is Metacity.

I have found that the wobbly windows effect works. I cannot say what other effects work or which ones will break the desktop.

You may want to read this thread:

[http://ubuntuforums.org/showthread.php?t=1892851]("http://ubuntuforums.org/showthread.php?t=1892851")

Regards.

---

### Post by Frogs Hair on 2012-05-16
There are plenty of examples of Compiz on Youtube also . [http://www.youtube.com/watch?v=AYukIoMmcMY](http://www.youtube.com/watch?v=AYukIoMmcMY)

---

### Post by sen0140 on 2012-05-16
Thanks for the replies, quick question I just downloaded the extra plug-ins and came across an animations add-ons, does it matter what kind of video card that I have in order to run some of these add-ons, because I can't see anywhere on how to use some of them especially the animation one, thanks.

---

### Post by dferriman on 2012-05-16
> **sen0140 said:**
> Thanks for the replies, quick question I just downloaded the extra plug-ins and came across an animations add-ons, does it matter what kind of video card that I have in order to run some of these add-ons, because I can't see anywhere on how to use some of them especially the animation one, thanks.

A modern graphics card should be fine. You don't need a $300 card, but you can't use it on one fits the bare requirements for installing Ubuntu either.

---

### Post by loklaan on 2012-05-16
> **sen0140 said:**
> Thanks for the replies, quick question I just downloaded the extra plug-ins and came across an animations add-ons, does it matter what kind of video card that I have in order to run some of these add-ons, because I can't see anywhere on how to use some of them especially the animation one, thanks.
You can change the effects for animations by going into **Animations** and clicking *Edit* on a selection. You can then change the effect from a dropdown menu! If you installed the extra you should also have an extra **Animations Add-On** that brings in more kind of effects.

Feel free to fiddle with the settings, you can always reset everything in CCSM by going to the Preferences and hitting *Reset to defaults*.

---

