---
title: "Coping /home to different hard disk"
date: 2011-02-26
forum: General Help
---

### Post by zedi on 2011-02-26
from: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Q. - "Next we will copy all files, directories and sub-directories from your current /home folder into the new partition:
sudo rsync -axS --exclude='/*/.gvfs' /home/. /media/home/."

I would like to know what the dots in /home/. and /media/home/. mean? 
Or to put it other way; will the command bellow copy my /home to /media/home (on different hard disk)?

sudo rsync -axvS --exclude='/*/.gvfs' /home/ /media/home/

---

### Post by doas777 on 2011-02-26
looks like a regex.

in Regular expressions, a period is a symbol for Any character, even whitespace.

in other uses, a . in a file name like in .gvfs hides the file.

in Shell (bash) . means the current working directory. the path returned by the command 'pwd'. most of the time when you see . in a command, thats what it means but it makes no sense in this context.

I personally have never used rsynch, but it probably simplifies preserving the ownership and permissions of the files, so you could just copy the files with the -r -P arguments. be sure to unmount any optical drives or network shares first though. thats what the exclude statement is for in your command.

---

### Post by billdozor on 2011-02-26
zedi: The command you typed will work. I use rsync everyday and it copies everything, even hidden files just fine in the syntax that you have above.

(sudo rsync -axvS --exclude='/*/.gvfs' /home/ /media/home/)

---

### Post by zedi on 2011-02-27
doas777 and billdozor many THX! Solved!
What about error in Ubuntu Community Documentation page?
Anybody knows how to edit:  [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

