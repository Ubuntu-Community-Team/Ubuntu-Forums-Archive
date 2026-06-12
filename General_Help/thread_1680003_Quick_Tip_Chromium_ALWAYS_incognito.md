---
title: "Quick Tip: Chromium ALWAYS incognito"
date: 2011-02-01
forum: General Help
---

### Post by Sutur on 2011-02-01
Not sure if it works for Ubuntu, only tested in Xubuntu.

If you're using docky, or gnome-do etc etc etc and can't make an incognito chromium shortcut, just edit the following files:

```

/usr/share/app-install/desktop/chromium-browser.desktop
/usr/share/applications/chromium-browser.desktop
```

Locate the exe lines:

```
Exec=chromium-browser %U
Exec=/usr/bin/chromium-browser %U
```

And modify them like so:

```
Exec=chromium-browser --incognito %U
Exec=/usr/bin/chromium-browser --incognito %U
```

Restart gnome-do/docky/whatever.

Done, Should be a setting for this.

---

### Post by d4m1r on 2011-11-01
Thanks!!! =D>

Worked like a charm on 11.04 Ubuntu w/Unity.

Used "sudo gedit /usr/share/applications/chromium-browser.desktop"

and modified the exec field to "Exec=/usr/bin/chromium-browser --incognito %U"

No restart of Unity needed, I have a Chromium shortcut on my Unity launcher, but just in case I went to the desktop and hit f5. :D

---

