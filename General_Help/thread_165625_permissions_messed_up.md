---
title: "permissions messed up"
date: 2006-04-24
forum: General Help
---

### Post by spartan777 on 2006-04-24
somehow, i've lost permissions to my very own desktop on one of my profiles. i can't write to my own desktop! my home folder is still fine, and looking in that, the desktop folder has a lock on it. when looking at the folder properties, the desktop folder has the same permissions as the home folder, only the permissions are all grayed-out, so I can't change a thing. the 'owner' has r/w/e permissions, which is weird. have I lost ownership of my own desktop or what?

also, a possibly related thing (since it started happening at the same time) is that only the original profile- the one created during installation, can do anything under system->administration. can't do updates, install printers, or anything admin unless i'm in the profile that has the desktop problems.

the only things i could possibly give these problems credit, are i installed the root-scripts using automatix, though the only things i've done with those are editing .conf files and such. another weird thing was that once i locked the screen (of aforementioned, problematic profile), switched user, and accidentally logged back in, after getting a 'are you sure you want to do this' warning. after doing this, my theme changed, and icons wouldn't load, like the 'trash bin', or 'show desktop' icons. after logging back out, and then in again, everything was normal, except any r/w access to the desktop is denied.  i have no idea how that may have affected permissions though.

the exact wording, besides the "[username]" bit:

Cannot move "/home/[username]/desktop/psswds.txt" to the trash because you do not have permissions to change it or its parent folder.

this was a long post, but i wanted to provide as much info as possible. thanks for the help in advance.

---

### Post by sinkxdie on 2006-04-24
I don't know which exact permissions to change,
But try this: do "alt+ctrl+F3(or an empty one)"
login as root
and type "startx" or whichever Desktop interface you use.

---

### Post by nanotube on 2006-04-25
hey
can you please post the output of
```
ls -ald /home/<username>/Desktop
```
and of
```
ld -al /home/<username>/Desktop/fileyouwanttodelete
```
(of course replace <username> with your actual username.)
and we will go from there.

---

