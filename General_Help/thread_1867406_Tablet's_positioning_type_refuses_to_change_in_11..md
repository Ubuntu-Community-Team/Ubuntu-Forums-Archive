---
title: "Tablet's positioning type refuses to change in 11.10"
date: 2011-10-22
forum: General Help
---

### Post by God of the Meeps on 2011-10-22
Hey everybody,

I recently upgraded to 11.10, and my mouse positioning broke - instead of using relative positioning, it uses absolute for both the mouse and then pen. It's an old tablet; a Graphire 4, I think. I read one post that I tried (going into dconf-editor and changing the is-absolute setting to false), but it didn't work for me, unfortunately. Help?

Thanks in advance.

---

### Post by Favux on 2011-10-22
To get this straight, when you go into dconf-editor then org.settings-daemon.peripherals.wacom.cursor, unchecking the box of is-absolute doesn't fix it?  Instead of going to Relative it stays Absolute?

I wonder if the Wacom Graphics Tablet control panel applet in System Settings is over riding the change?  In which case that is a bug and you should report it to Gnome.  As you notice this first version, appearing for the first time in GNOME 3.2, is rather limited.

Since gnome-settings-daemon settings override any static Option you won't be able to fix it with a wacom.conf or the xorg.conf.  So that leaves xsetwacom.

Try:
```
xsetwacom set "device name" Mode Relative
```
Where <device name> is the name you get for the Wacom tablet mouse (i.e. cursor) from *xinput list*.

---

### Post by God of the Meeps on 2011-10-22
I was looking in a similar thread that you posted in as well, just now, haha. 

Thanks for the reply! It works now.

---

