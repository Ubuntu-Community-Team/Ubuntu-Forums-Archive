---
title: "Can't customized mouse any more..."
date: 2011-07-08
forum: General Help
---

### Post by Alchaggy on 2011-07-08
Hi everyone, I installed xubuntu 11.04 in my toshiba laptop, is running awesome!, but I started to customized some things in the xfce desktop, so I was trying to change the mouse look because y changes only in the desktop and not in the other windows. I read in other posts (I don't remember them right now) to do the following:

Open Terminal and Type: sudo gedit /usr/share/icons/default/index.theme

and then in the pop-up window will appear 

[Icon Theme]
Inherits=DMZ (White)

so that was the thing I had to change...

I did it and it work once... I change it to the black one the first time, but second one to a cursor I downloaded, it was a mac cursor.
The point is it screw up my desktop I had to remove it and start the again the process "xfwm4", but after I change it the mouse theme is now a very ugly black mouse, with ugly forms and shapes, not like the DMZ (Black)...

Any Idea of how get back my dmz black cursor o the white one again?????:confused:

---

### Post by Rodney9 on 2011-07-09
Have you tried the obvious, in Settings - Settings Manager - Mouse and then Theme tab.

---

### Post by Alchaggy on 2011-07-09
> **Rodney9 said:**
> Have you tried the obvious, in Settings - Settings Manager - Mouse and then Theme tab.

Obviously if the easiest way didn't work you have to look for other options!!! you "Rodney9 Master of the Obvious":mad:

---

### Post by SRved on 2012-02-06
I ran into exactly the same problem when trying to customize my Xubuntu. I wanted to use the excellent Comix mouse theme.

I first went to [http://gnome-look.org/content/show.php?content=32627](http://gnome-look.org/content/show.php?content=32627) to get the ComixCursors X11 mouse Theme. (I got the "ComixCursors-0.7.3.tar.bz2" one).

Once the file containing LOADS of themes had downloaded, I extracted the (50!!!) cursor theme folders, and selected the "ComixCursors-White-Regular" folder.

sudo copy the ComixCursors-White-Regular Folder to /usr/share/icons/  (I use Terminal - sudo thunar)
there should also be DMZ-Black and DMZ-White folders in there.

goto Start Menu > Settings > Settings Manager.
Select Mouse, then the Theme Tab. it should now have "Comix Cursor original White Regular Bold" in the list. Select it.
Since there is no apply button and the pointer doesn't change, it seems not to have done anything.
(but at this point, some opened windows (firefox, leafpad, etc) will have the Comix theme, but the windows and panels will have a default pointer (I think DMZ-White) still.)

sudo leafpad /usr/share/icons/default/index.theme    (Use editor of choice)
On my default Xubuntu 11.10 install, it read:
[Icon Theme]
Inherits=DMZ-White

Change it to:
[Icon Theme]
Inherits=ComixCursors-White-Regular

NOTE: it seems to be the Folder name, not the name given in the Mouse Theme list.

(this next bit might not be needed:)
I noticed that the DMZ-White folder has a cursor.theme which the Comix folder didn't have.
it had the same Inherits=DMZ-White as above, so I (sudo) copied it over and (sudo) edited the copied one to Inherits=ComixCursors-White-Regular.

Reboot (logout doesn't seem enough) and when it kicks back up, you should (fingers crossed) have your nice cursor in everything! :)

PS. Apologies for the rambling approach; I prefer loads of description to terseness... lol

---

