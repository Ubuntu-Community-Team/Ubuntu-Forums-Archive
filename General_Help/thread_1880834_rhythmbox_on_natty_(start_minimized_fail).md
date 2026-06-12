---
title: "rhythmbox on natty (start minimized fail)"
date: 2011-11-14
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-11-14
This is really driving me nuts
it looks like someone did not like one of my favs features in it
[https://bugzilla.gnome.org/show_bug.cgi?id=537868](https://bugzilla.gnome.org/show_bug.cgi?id=537868) (they created a regression imho)
but nothing i have tried makes it minimize to the Notification Area i can't even get it with devilspie (ends up on my window preference list) on top of this rhythmbox-client --hide does nothing (even tried to install lucid's rhythm-box -failed-)

for the record i am am using rhythmbox since banshee does not want to see my music in my music folder

---

### Post by Tamlynmac on 2011-11-14
In the gnome configuration editor.
configuration editor/apps/Rhythmbox/status-icon

If the status icon is "active" (box checked) and the "window-visible" is  unchecked the icon will appear in the notification section of your  panel.

If the status icon is not "activated" (box unchecked) and/or the "window-visible" is checked it will not appear.

Once it appears in the notification area, closing Rhythmbox will leave  the icon in the notification area. To remove it from the notification  area you must left click on the icon and select "Quit". You can open the  window by left clicking on the icon and close the window (back to icon  by hitting the "X" and closing it). If your playing music it will  continue until the notification icon is "Quit". Which then removes the  icon and actually closes the app.

I'm not quite certain if thats what your asking, but hope it helps.

---

### Post by pqwoerituytrueiwoq on 2011-11-15
want it to open/launch as the try icon and not show the window
[FONT=Courier New]rythmbox-client --play --hide[/FONT] should open the it minimized and playing but it is not minimized

---

### Post by Tamlynmac on 2011-11-15
Have you tried checking the box next to "active" and uncheck the window-visible box in the gnome config editor?
configuration editor/apps/Rhythmbox/status-icon

The gnome configuration editor is located in the "Systems Tools" menu.

There's no reason to hide it. if you open the window from the taskbar icon, just close the window and the icon will remain in the taskbar next to the notification area. To get rid of the icon, just left click on the icon and select "Quit". Which will close the app.

---

### Post by pqwoerituytrueiwoq on 2011-11-15
yes i have those options set like that did when i made the thread
back in lucid when you closed whythmbox when it was minimized to tray the net time you open it it would be minimized to tray and nto show the window but this feature was removed in a later version if that featrie was not removed i could have [FONT=Courier New]rhythmbox-client --play[/FONT] as a start up entry and have it play as soon as i login and not have to close a window

---

