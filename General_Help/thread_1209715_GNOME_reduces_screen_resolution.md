---
title: "GNOME reduces screen resolution"
date: 2009-07-10
forum: General Help
---

### Post by gilch on 2009-07-10
Upon booting the screen resolution is OK (as witness the size of the arrow cursor during bootup). This would mean to me that NVIDIA configured the resolution as it should have. But once GNOME starts, it reduces the resolution. I then have to set it up right using NVIDIA config. But as soon as I reboot, the same thing repeats. Can I configure GNOME to set the resolution right. Where would I do that?  (Rather newbee)
Gilles

---

### Post by doas777 on 2009-07-10
well it shoudl be under system -> preferences - > screen resolution. 
I believe the bin name is 'displayconfig-gtk'

on at least one kernel on one box, I had to make sure that both the nvidia-settings and the displayconfig were both set to the same res, or I'd get a blackscreen

---

### Post by gilch on 2009-07-10
The closest i have to this is System>Preferences>Display.
Then it refers me to my graphics vendors tool, which doesnt help.

---

### Post by doas777 on 2009-07-10
try hitting Alt+F2 and enter:
```
displayconfig-gtk
```

---

### Post by gilch on 2009-07-10
Response:
Error stating file '/home/gilles/displayconfig-gtk': No such file or directory

---

### Post by doas777 on 2009-07-10
hmmm. that sucks. I'll look at it after i get home. no ubunutu here...
good luck

---

### Post by gilch on 2009-07-12
Finally, someone posted a solution to my problem (in Nvidia forums).
That was to add 'xrandr -s 1280x800' (for me it was 1920x1080) to the startup list.
This works. I hope it works for you as well. This closes this thread for me.
Gilles

---

