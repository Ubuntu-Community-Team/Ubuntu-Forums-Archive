---
title: "Missing Disk Space"
date: 2009-09-29
forum: General Help
---

### Post by qwwerty on 2009-09-29
Ubuntu is showing it's partion as full, but not showing any data in over half of it. It now won't write to the disk, reporting there isn't enough data. Does anyone know how I can get my space back?

Edit: Added screenshot of Disk Analyser, showing the problem.

---

### Post by blueridgedog on 2009-09-29
Can you post the output of 
```

sudo fdisk -l 
```

and 

```
df
```

and identify the partition that you can not write to?

---

### Post by drs305 on 2009-09-29
The screenshot attachment isn't showing up yet. 

In the meantime, this guide may help:
[HOWTO: Recover Lost Disk Space  ]("http://ubuntuforums.org/showthread.php?t=1122670")

You can probably get a bit of space by running 
```

sudo apt-get clean

```
to clear the package cache.

Normally, disks fill up with backups to the wrong partition, undeleted trash (including root's) or 'runaway' log files.

---

### Post by Megrimn on 2009-09-30
how long has it been since you emptied the trash bin?  just a suggestion :)

---

### Post by qwwerty on 2009-09-30
Found the problem, there's a load of files in Root, that Disk Analyser didn't show.

Does anyone know how to remove them, I tried to delete them from nautilus (running as root), but they didn't delete. Any ideas?

---

### Post by drs305 on 2009-09-30
> **qwwerty said:**
> Found the problem, there's a load of files in Root, that Disk Analyser didn't show.

Does anyone know how to remove them, I tried to delete them from nautilus (running as root), but they didn't delete. Any ideas?

So you started nautilus with "gksu nautilus" or "gksudo nautilus"?
If that's how you started it, you should be able to highlight the files and then use SHIFT-DEL to remove them. If you just hit DELETE, they recycle to the Trash again.

The other way is to use "sudo" combined with the "rm" command but this can be a very dangerous way to delete things. A typo could erase most of your system.

---

