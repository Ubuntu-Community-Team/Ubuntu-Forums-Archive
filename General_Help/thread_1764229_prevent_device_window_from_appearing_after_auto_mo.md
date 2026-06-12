---
title: "prevent device window from appearing after auto mount at startup?"
date: 2011-05-21
forum: General Help
---

### Post by thexnightmare on 2011-05-21
Dear,
When running ubuntu, a window open automatically for my BD disc and USB Hard disk.
How can I prevent this windows to be shown but keep the auto mount option of cdrom and USB hard disk?
Thx

---

### Post by Tamlynmac on 2011-05-21
I'll  assume your still running 9.10.

If so, and your not using any icons on your desktop you could open the gnome configuration editor (locate in your system tools menu). 

Then open apps/nautilus/preferences and uncheck your "show_desktop" in the preference (right window). Left click on the box one time to switch between checked & unchecked. This prevents any icon from being placed on your desktop. It will have no effect on your panel or any apps. Should you want icons on the desktop, just go back and check the box (anytime).

If I recall correctly in 9.10 the only ofter issue with this is - it may not permit right clicking on the desktop to open the shortcut to the appearance (screensaver) window. Which means you would need to open the system preferences menu to go to the appearance window. It's no big deal, but nice to know ahead.

I might suggest, if your going to continue using any versions prior to 11.04 that you look through the gnome configuration editor as there's many alternative configuration options available in the editor. Most all of which can be turned on/off or altered as required.

Good Luck & hope this helps.

---

### Post by thexnightmare on 2011-05-21
Actully, I just upgraded to 10.04 LTS.
Thx for your answer, however, I am not asking about the icons which appears on the desktop, but about the window which opens and show the files of this drive.

---

### Post by Tamlynmac on 2011-05-22
I'm sorry - misunderstood.

The window that opens is probably the  file browser which is setup in Nautilus. In your menu open "places/home  folder", and select "edit/preference". When the preference window opens  go to the "media tab".

There you can select what you want to  happen when the system detects inserted media. One of the individual  selectable options from the drop down menus, should be to "do nothing"  or you can select to open other apps which are generally located in
file system/usr/bin.

Is that what your looking for?

---

### Post by thexnightmare on 2011-05-22
Yeah thx.

---

