---
title: "can I mount --bind to /media?"
date: 2010-09-28
forum: General Help
---

### Post by UncleBoarder on 2010-09-28
I want to mount a subtree to the desktop and have it's icon appear as an internal drive/volume.

If I could do this as a symLink, that's a reasonable workaround but I want the icons to be identical to my other internal drive already mounted to /media.  And I don't know how to change icons.

My preference is to do something like this (but it doesn't work of course)

[FONT=Fixedsys]/mnt/shared/Ubuntu /media/data bind defaults,bind 0 0[/FONT]

I've noticed that you can't remount the same device twice to /media.  And the mount to /media has to be first otherwise it will mount but not display on the desktop.  These two problems appear to make my goal impossible.

So, how do I get my subtree to display on the desktop with an icon for an internal drive?  Oh, and it needs to happen at boot.

---

### Post by gzarkadas on 2010-09-29
It is better to just create a launcher (right-click with the mouse onto the desktop and select `Create Launcher...' from the pop-up menu that appears) with the following properties:

_Name:_ The name of your share as you want it to appear at the desktop
_Command:_ nautilus [path-to-your-share]. For example:
```
nautilus /mnt/shared/Ubuntu
```Then click the icon at the left side of the dialog box and, from the new dialog box that appears, click the `Browse...' button at the top-right and in the new (third) dialog box navigate to directory `/usr/share/icons/gnome/scalable' directory. There select directory `devices' from the listbox at the left and click the `Open' button. The third dialog box will close and a view of the icons inside `/usr/share/icons/gnome/scalable/devices' will show at the second dialog box, below the `Browse...' button. Select from these the `gnome-dev-harddisk.svg' icon.

Now, the good news: after you have done this once you can copy the desktop launcher to other user accounts' desktops and even to new user accounts' desktops (put a copy of the launcher inside /etc/skel/Desktop - or your localised name for Desktop). Just fix the ownership and permissions after the copy with `chown' and `chmod' respectively.

---

### Post by UncleBoarder on 2010-09-29
Awesome!

Works great and it's exactly what I want.

I learned a lot on that one.

Thanks!!!!!!!!!

---

### Post by gzarkadas on 2010-09-29
You are welcome :). 

I forgot to note that if you use a symlink then you are "transferring" your tree under the Desktop (which in your case I figured it wasn't what you wanted). But if you do, then symlinks can also change icon by right-clicking, selecting "Properties" from the pop-up menu and clicking the icon at the left. Only that this time you have to navigate down to the icon file and press `Open'; there is no list with icons to choose as in the previous case.

---

