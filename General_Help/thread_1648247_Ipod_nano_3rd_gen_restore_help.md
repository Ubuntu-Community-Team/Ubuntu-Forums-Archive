---
title: "Ipod nano 3rd gen restore help"
date: 2010-12-18
forum: General Help
---

### Post by evolmachine on 2010-12-18
I'm trying to restore my ipod nano 3rd gen.  Banshee, rhythmbox, and gtkpod do not work properly so I've resorted to using virtualbox and windows xp with itunes.

My problem is I can only mount the ipod in virtualbox once per boot.  If i have to unplug it i have to completely restart my computer to get the ipod to be mounted again.  

oddly, this is only a problem after I launch virtualbox.  I can unplug and plug in my ipod as many times as i want in ubuntu and it'll mount every time.  However, as soon as I launch virtualbox I get one chance in windows vm and then its gone.  even if I close virtualbox I can't get ubuntu to see my ipod.

Any help on this would be greatly appreciated.

---

### Post by evolmachine on 2010-12-18
figured it out.

Restarted computer.  Used Disk Utility to format iPod format drive with No Partitions as Fat filesystem.  Fired up Virtualbox and iTunes and did a restore from there.  Worked this time.  

USB stuff works properly now.

---

