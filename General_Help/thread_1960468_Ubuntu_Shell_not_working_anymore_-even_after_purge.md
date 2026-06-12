---
title: "Ubuntu Shell not working anymore -even after purge"
date: 2012-04-17
forum: General Help
---

### Post by airspoon on 2012-04-17
Hello, 
I just installed a fresh Ubuntu 11.10 after building a new PC. I then installed Gnome Shell and everything seemed to be working fine until I installed a shell extension that gives the read-out of processor temps. After installing that extension, my task bar went away and all I could see is the wallpaper -that's it.

So I then tried to purge the Gnome Shell install and the extensions with the following command:
```

sudo apt-get purge gnome-shell-* gnome-shell

```

That seemed to work fine, considering that I no longer had the Gnome option on the loggin screen. However, after trying to re-install Gnome Shell, it's still not working and I'm only able to see the wallpaper. Is there something I'm not doing right?

In case it matters, my computer is an i5-2500k on an AsRock Z77 E6 Motherboard with 8 gigs of RAM and a Sandisk Extreme 120GB SSD.

Any and all help would be greatly appreciated. I'm just used to working on Gnome Shell and no matter how hard I try, I just don't like Unity, as it severely impedes my work-flow. again, thanks for any and all help.

---

### Post by airspoon on 2012-04-17
Is it that I may have not completely uninstalled Gnome Shell? Is there someway that I could completely remove it (and the extensions)?

---

### Post by fotis_utmost on 2012-04-18
Same problem here. Gnome-shell was working fine, except of some momentary freezes, and suddenly it crashed. I didn't even install a new extension. Tried to uninstall it and re-install it, but the problem persists...

Anyone?

---

### Post by fotis_utmost on 2012-04-18
I have an ATI card and tried to purge fglrx and re-install the ati driver. Everything back to normal.

---

### Post by alex2e1gzy on 2012-04-18
Iv'e had a number of issues with the ATI Drivers and Gnome Shell. It seems to be a problem in 11.10:

[http://ubuntuforums.org/showthread.php?t=1872158&page=2](http://ubuntuforums.org/showthread.php?t=1872158&page=2)

---

### Post by kurt18947 on 2012-04-18
gnome shell extensions often reside in /home/share/gnome-shell/extensions though not always.  I had a problem with one extension causing the desktop to not redraw.  I logged out, logged on in either Ubuntu (Unity) or Xfce, navigated to the proper directory, deleted the problem extension and restarted just for luck.  That fixed it.

---

### Post by airspoon on 2012-04-18
@Kurt18947
Thanks for your reply and help. I looked for that directory but couldn't find a /home/share/ directory. Could they reside in another directory possibly?

@Fotis_utmost

Thanks also for your reply. I don't have an ATI graphics card. I'm using the integrated Sandybridge graphics. You think it could be a problem with my proprietary drivers? I don't think I had any installed when Gnome Shell suddenly stopped working. Since then however, I have installed Epson's Linux driver for their "all-in-one".

---

### Post by kurt18947 on 2012-04-20
> **airspoon said:**
> @Kurt18947
Thanks for your reply and help. I looked for that directory but couldn't find a /home/share/ directory. Could they reside in another directory possibly?

@Fotis_utmost

Thanks also for your reply. I don't have an ATI graphics card. I'm using the integrated Sandybridge graphics. You think it could be a problem with my proprietary drivers? I don't think I had any installed when Gnome Shell suddenly stopped working. Since then however, I have installed Epson's Linux driver for their "all-in-one".

I forgot part of the path, sorry.  It should be 'username'/.local/share/gnome-shell/extensions.  I reveal the hidden .files in Nautilus by holding <Ctrl>h.  Not all extensions are found there but  in my experience any extension installed from gnome's web site is found there.

---

