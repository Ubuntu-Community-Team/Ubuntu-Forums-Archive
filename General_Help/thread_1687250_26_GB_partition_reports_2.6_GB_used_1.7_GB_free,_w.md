---
title: "26 GB partition reports 2.6 GB used 1.7 GB free, where is the rest?"
date: 2011-02-13
forum: General Help
---

### Post by TheCat on 2011-02-13
I've mounted /home on its own 26 GB partition.  I have 2.6 GB of files in /home/chris/.  The only other thing in /home is /home/lost+found/ which appears to be empty.  Nautilus reports that there is 1.7 GB free.  Where is the rest of my disc?  I'm confused. :confused:

---

### Post by An Sanct on 2011-02-13
Did you check this out with gparted?

If you haven't downloaded it yet, it can be found in the software center.
After that, it is in system -> administration -> gparted partition editor

---

### Post by TheCat on 2011-02-13
Yes, gparted also shows it as a 26 GB partition.

On a whim, I just emptied the trash.  Now it shows 18.1 GB free.  That's still only a total of 20.7 GB, which leaves 5.3 GB unaccounted.

Why does the trash consume disc space when Nautilus reports free space?  Shouldn't that space be available?

---

### Post by uRock on 2011-02-13
System> Administration> Disk Utility or System> Administration> System Monitor> Files Systems tab will show complete data of Partitions size and usage.

GParted will work for finding this info, but isn't really necessary.

TheCat, can you take a screenshot of System Monitor showing this info? 

To take a screenshot, go in the menus to Applications> Accessories> Take Screenshot, then select Grab the Current Window and set the timer to one or more seconds.

To attach the screenshot, click the little paper clip in the reply ribbon.

---

### Post by uRock on 2011-02-13
> **TheCat said:**
> Why does the trash consume disc space when Nautilus reports free space?  Shouldn't that space be available?
The items in Trash will consume space until the files are deleted from Trash.

---

