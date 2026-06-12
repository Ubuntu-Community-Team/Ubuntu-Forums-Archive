---
title: "Kile icon missing from KDE menu"
date: 2011-10-10
forum: General Help
---

### Post by WebDrake on 2011-10-10
With both 11.04 and 11.10 a strange thing happens: the Kile entry in the KDE system menu no longer has the round blue Kile icon next to it, only the "blank page with a question mark" that indicates no icon has been found.

Can anyone advise how to restore the icon?  The same does not occur with Ubuntu/Unity.

---

### Post by WebDrake on 2011-10-10
I've attached a couple of screenshots, the first from the edit menu settings; the second of the actual menu.

It's bizarre, because the Kile icon shows up in settings -- but not next to the Kile entry in the menu.  Any suggestions what's wrong?

---

### Post by dniMretsaM on 2011-10-10
Try changing the owner of the .desktop (I think the path would be /share/app-install/desktop/kile.desktop) configuration file to you with this command in terminal:
```
sudo chown yourusername:yourusername /path/to/kile.desktop
```Then open up properties of the Kile (from the application menu) and change the icon to the correct one. It's possible that it won't show up so you may have to download the Kile icon (from Google Images or something), save it as a .png, and use that as the icon. I had an issue similar to this with Eclipse.

---

### Post by WebDrake on 2011-10-10
> **dniMretsaM said:**
> Try changing the owner of the .desktop (I think the path would be /share/app-install/desktop/kile.desktop) configuration file ... Then open up properties of the Kile (from the application menu) and change the icon to the correct one.

Thanks for the suggestion; I tried, to no avail. :-(

I am not sure this can be the issue -- as you can see from the application settings screenshot, the Kile icon is present and associated with the Kile menu entry, it's just not appearing in the menu itself.

---

### Post by dniMretsaM on 2011-10-10
That's what had me confused before. The icon shows up on the properties screen, but no where else. Try changing it to a different icon (one you know shows up like the Firefox icon or something) and see if that works. This might be a different issue, but it sounds very similar. You can read the thread about it [here](http://ubuntuforums.org/showthread.php?t=1832979).

---

### Post by WebDrake on 2011-10-11
Yea, selecting "Other icons" and then one (any) of the kile.png files found in /usr/share/icons/hicolor/ worked.  Very bizarre.

Thanks very much for the support & advice!

---

