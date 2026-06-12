---
title: "Browser bookmarks"
date: 2011-06-19
forum: General Help
---

### Post by Draike_ on 2011-06-19
Firefox has stopped saving bookmarks.The bookmark tab will not display.

---

### Post by lovinglinux on 2011-06-20
Close Firefox, then delete the file *places.sqlite* (make a backup first) from your Firefox profile folder under ~/.mozilla/firefox/<profilename>/. Then start Firefox, open the Bookmark manager (CTRL+SHIFT+O), click *Import and Backup*, then *Restore* and select the latest backup.

---

### Post by Draike_ on 2011-06-21
I am unable to find the places.sqlite file.which folder is it in.I have tried to find the firefox folder also.

---

### Post by lovinglinux on 2011-06-21
> **Draike_ said:**
> I am unable to find the places.sqlite file.which folder is it in.I have tried to find the firefox folder also.

Open your user home folder, hit CTRL+H to display hidden files, open the folder *.mozilla*, then *firefox*, then the profile folder, which probably has *default* in the name.

---

### Post by Draike_ on 2011-06-22
Thank you.The bookmarks toolbar does not show up but I can save bookmarks to the bar at the top of the screen and access them.

---

### Post by dino99 on 2011-06-22
try in a terminal: sudo dpkg-reconfigure firefox

---

### Post by Draike_ on 2011-06-22
That worked fine.Thank you both for your help.

---

### Post by fly135 on 2012-03-19
> **dino99 said:**
> try in a terminal: sudo dpkg-reconfigure firefoxJust to let people know... This was the only fix for me.  Nothing else worked.

---

### Post by daslinkard on 2012-03-19
That is not surprising as the Terminal can allow for you to go to beast mode!  However they gave you some excellent, and I do mean, EXCELLENT advice.  Glad it is fixed for you!

---

