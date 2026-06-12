---
title: "list files of a certain age and copy?"
date: 2006-03-07
forum: General Help
---

### Post by chaumurky on 2006-03-07
I want to backup files in /etc that have been modified recently before I reinstall ubuntu. What would be a nice command to list them and then pipe that to a copy them to another folder?

---

### Post by aysiu on 2006-03-07
```
ls -lt
``` will list them by last modified.
You can do this graphically, too, if you just search for them with ```
gnome-search-tool
``` and then sort by last modified.

---

### Post by chaumurky on 2006-03-07
Is that first line recursive? Also I want to keep the folder structure so that after the reinstall I can see where they need to go. How can I pipe the output to,say, a cp command?

EDIT: I should have been more precise. I want to be able to specify and list files of a certain age and copy them.

---

### Post by aysiu on 2006-03-07
Your best bet is ```
sudo cp -R /etc /destination_directory
``` Then do a search of the destination directory using *gnome-search-tool* (a graphical app), sort by modification date, and delete the oldest stuff.

---

### Post by chaumurky on 2006-03-07
OK, I'm getting somewhere. I've discovered **sudo find /etc -mtime <n> | grep conf** does what I need for the listing. How do I pipe the output to a cp command?

---

### Post by aysiu on 2006-03-07
No idea.

---

### Post by chaumurky on 2006-03-07
It's pretty convoluted. At least it works.
[B]
sudo find /etc -mtime -<n> | grep conf | tar -cf - -T - | gzip > ~/conf.tar.gz[/B]

---

