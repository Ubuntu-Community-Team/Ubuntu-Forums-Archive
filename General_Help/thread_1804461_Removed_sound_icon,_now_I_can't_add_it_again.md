---
title: "Removed sound icon, now I can't add it again"
date: 2011-07-14
forum: General Help
---

### Post by rva1945 on 2011-07-14
How do I add the icon again?

I was trying to fix this problem: headsets are not detected when plugged and the sound is not re-directed to the headsets, and I followed some directions from this forum, I removed the icon but now I can't add it again.

if I right-click on the panel, then Add to panel... the icon is not in the list.

Anyway, anybody knows how to fix the headsets jack sense issue? My notebook is a Lenovo.

Thanks

---

### Post by mike555 on 2011-07-14
I found this when I was in search of a resolution to the same problem. And it seems to work:

go to System > Preferences > Startup Applications

in the startup tab, look for 'Volume Control' and check it if its unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

...and then restart....

---

### Post by CatKiller on 2011-07-14
> **rva1945 said:**
> if I right-click on the panel, then Add to panel... the icon is not in the list.

If you're using 11.04, it's "Indicator Applet Complete" that you'll want to add back to the panel.

---

### Post by rva1945 on 2011-07-15
> **mike555 said:**
> I found this when I was in search of a resolution to the same problem. And it seems to work:
 
go to System > Preferences > Startup Applications
 
in the startup tab, look for 'Volume Control' and check it if its unchecked.
 
If its not there, 'Add' it using the following parameters:
 
Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control
 
...and then restart....
 
Thanks but I don't understand what I have to do with that Name, Command and Comment.

---

