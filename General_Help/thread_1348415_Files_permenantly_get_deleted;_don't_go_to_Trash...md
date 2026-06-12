---
title: "Files permenantly get deleted; don't go to Trash..."
date: 2009-12-07
forum: General Help
---

### Post by emigrant on 2009-12-07
hi all,
if i delete a file from the desktop or somwehre, it get deleted permanantly without going to the trash.
how can i solve this?

thank you very much for your help.

---

### Post by x33a on 2009-12-07
Do you choose move to trash or delete option?

Also, if you running nautilus as root for whatever reason, the deleted files will go to root's trash.

---

### Post by emigrant on 2009-12-07
im running nautilus as normal user and i did both move to trash and delete key. both lead to same results.

---

### Post by x33a on 2009-12-07
move to trash should move the deleted files to the trash folder.

and delete will directly delete the files without moving them to the trash.

Try installing a package called trash-cli. it is a commandline software which can move files to trash. see if it manages to move the files to trash, and post the result here.

or try some other file manager, such as thunar or pcmanfm, etc.

---

### Post by emigrant on 2009-12-07
i did a fresh jaunty install and still have the problem.  [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG] [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

if i do -->

```
emigrant@emigrant-desktop$ cd /home/emigrant/.local/share/Trash/
emigrant@emigrant-desktop:~/.local/share/Trash$ ls
files  info

```

i can see the file info i just deleted. but how to make them visible in the original Trash?  [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

thank you very much

---

### Post by emigrant on 2009-12-07
thanks all, rebooting solved the problem :)

---

