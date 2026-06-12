---
title: "Ctrl+alt+F10 problem"
date: 2010-06-28
forum: General Help
---

### Post by fcoroa on 2010-06-28
So I was messing around in Ubuntu and I pressed ctrl+alt+f10 and my screen went all black... I paniced and pressed the reset button and now it says "no bootable partition" during boot... Does anyone have a solution?

Thanks a lot

---

### Post by TeoBigusGeekus on 2010-06-28
Boot with a live cd and fsck your partitions.

---

### Post by fcoroa on 2010-06-28
Thanks! I'll try that and then post back!

---

### Post by Ryan Dwyer on 2010-06-28
By the way, the Ctrl + Alt + Function keys allow you to toggle to different TTYs. Ctrl + Alt + F7 would have taken you back to the GUI.

---

### Post by fcoroa on 2010-06-28
I ran fsck on my ubuntu partition and it didn't work... Also I'm kind of new to the whole ubuntu scene... I'm pretty sure I did it right, though I don't think the Ubuntu CD I used is a live cd... I just used the option "try ubuntu without making any changes" and opened the command line from ubuntu's gui... Should I try and force fsck on reboot or fsck all partitions?

---

### Post by TeoBigusGeekus on 2010-06-29
Yes, you should.
By the way, it IS a live cd.

---

### Post by jperelli on 2010-06-29
be sure to fsck your ubuntu disk partition, and not your live cd (virtual) ram partition.

---

