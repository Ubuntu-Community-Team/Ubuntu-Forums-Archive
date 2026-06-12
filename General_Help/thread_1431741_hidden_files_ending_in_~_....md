---
title: "hidden files ending in ~ ..."
date: 2010-03-17
forum: General Help
---

### Post by rebeltaz on 2010-03-17
Why does Ubuntu keep creating copies (I assume backups) of files, marking them hidden and appending the ~ character to the end of the filename and how can I tell it to quit? 

I wouldn't mind if these files would be moved/deleted when the original file that they are associated with is acted on, but instead, I have a directory full of ~ files whenever I select to see hidden files, all belonging to files that I long ago deleted....

---

### Post by amauk on 2010-03-17
assuming gedit
edit > prefs > editor
uncheck "create a backup"

---

### Post by kaibob on 2010-03-17
Ubuntu creates backup copies of such files as xorg.conf. On my Ubuntu partition, there were 15 such files. I suspect the large number of backup files on your drive are being created by an application program not the OS. Without further information as to the file type and location, it's hard to say.

---

### Post by dcstar on 2010-03-17
> **amauk said:**
> assuming gedit
edit > prefs > editor
uncheck "create a backup"

And this is also the "solution" to trying to use gedit on NTFS filesystems that cannot handle hidden filenames (because of the leading ".").

---

### Post by rebeltaz on 2010-03-17
> **amauk said:**
> assuming gedit
edit > prefs > editor
uncheck "create a backup"

Thank you... I figured it was something easy like that :)

---

### Post by lisati on 2010-03-17
> **amauk said:**
> assuming gedit
edit > prefs > editor
uncheck "create a backup"

+1

(The "~" in this context is an equivalent of the ".bak" file type in MS-DOS and Windows.)

---

### Post by satish_j on 2010-03-17
> **amauk said:**
> assuming gedit
edit > prefs > editor
uncheck "create a backup"

Thanks...:):)

---

