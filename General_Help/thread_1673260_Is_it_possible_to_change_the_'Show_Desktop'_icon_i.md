---
title: "Is it possible to change the 'Show Desktop' icon in GNOME?"
date: 2011-01-22
forum: General Help
---

### Post by Rytron on 2011-01-22
Hi.

Is it possible to change the 'Show Desktop' icon in GNOME without change the Icon set? Or is there an alternative show desktop icon available?

Pictures: Ignore the second show desktop icon in 'show desktop-right click.gif' - I was just testing things out. In the second picture, the show desktop icon looks odd when you hover the mouse over it.

I have the panel pixels at the 22 and prefer it that way.

---

### Post by Vaphell on 2011-01-22
quick glance at theme directory indicates that one of these is responsible (though i didn't try to hard, maybe there are other copies of that icon):
/usr/share/icons/Humanity/places/<size>/gnome-ccdesktop.svg
/usr/share/icons/Humanity/places/<size>/gnome-desktop-config.svg
/usr/share/icons/Humanity/places/<size>/gnome-fs-desktop.svg
/usr/share/icons/Humanity/places/<size>/other-desktop.svg
/usr/share/icons/Humanity/places/<size>/user-desktop.svg


i think you have 2 possibilities
- replace in /usr/share/...
- override the icon by placing new one in ~/.icons (/usr/share/icons/Humanity/... -> ~/.icons/Humanity/...) - i think this one is better because it's non-destructive

---

### Post by Rytron on 2011-01-22
Hi Vaphell. No joy. There was no desktop.svg to replace in ~/.icons and the one in /usr/... had a shortcut icon on it. :???:

The theme I am using is **ubuntu-mono-dark**.

Update: I replaced user-desktop.svg in /usr/share/icons/Humanity/places/22 as you previously stated. It worked.

---

