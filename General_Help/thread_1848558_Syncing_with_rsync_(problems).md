---
title: "Syncing with rsync (problems)"
date: 2011-09-22
forum: General Help
---

### Post by marklovescoffee on 2011-09-22
I've been trying to use rsync to copy my home directory to an external hard drive. I researched commands and think this should be right, but it's not working. Can someone tell me what I'm doing wrong?

Entered in command line:
rsync -av /home/mark /media/Mark's Backup

(the first part is my home directory and the second part is the name of my external hard drive)

Is there something obvious I'm doing wrong? Sorry, I'm new to command line.

Thank you in advance.

---

### Post by patryk77 on 2011-09-22
Try
```
rsync -av /home/mark /media/Mark\'s Backup
```

At the very least, you need to escape quotes with the backslash (\).

---

### Post by oldfred on 2011-09-22
If Mark's Backup is the label you gave it and it gets automounted then it should work with quotes. Since converting to Linux I stopped using spaces and even Windows does not accept some special characters. I use CamelCase or Under_score as styles for labels or mount points. Linux is also case sensitive.

rsync -av /home/mark /media/'Mark's Backup'

There also are ways to add a space with escape and the 040 ACSII character but I never do that, so I do not know it.

An example of a bash file to do backups with some explanations:
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

---

### Post by marklovescoffee on 2011-09-22
> **patryk77 said:**
> Try
```
rsync -av /home/mark /media/Mark\'s Backup
```

At the very least, you need to escape quotes with the backslash (\).

Ah, I had a feeling it was something stupid like that! I'll try that right now, thanks.

From what I understand, I can just run this command whenever I plug in my hard drive and it will sync it with my home folder (delete deleted files, add new files, and change changed files)?

---

### Post by patryk77 on 2011-09-22
> **patryk77 said:**
> Try
```
rsync -av /home/mark /media/Mark\'s Backup
```

At the very least, you need to escape quotes with the backslash (\).


Oops... you should also at least escape the space

```
rsync -av /home/mark /media/Mark\'s\ Backup
```

@oldfred: I believe you mean:
rsync -av /home/mark /media/"Mark's Backup"

As 3 single quotes would be considered incomplete?

---

### Post by marklovescoffee on 2011-09-22
> **oldfred said:**
> If Mark's Backup is the label you gave it and it gets automounted then it should work with quotes. Since converting to Linux I stopped using spaces and even Windows does not accept some special characters. I use CamelCase or Under_score as styles for labels or mount points. Linux is also case sensitive.

rsync -av /home/mark /media/'Mark's Backup'

There also are ways to add a space with escape and the 040 ACSII character but I never do that, so I do not know it.

An example of a bash file to do backups with some explanations:
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

Putting in quotes worked! Thanks!

---

### Post by oldfred on 2011-09-22
@patryk77 of course you were correct and marklovescoffee must have used double quotes. Part of why forum works as even if we miss one thing someone else fixes it.

marklovescoffee - glad it worked.

Script will not run automatically when you plug it in if it is just a script. Not sure where you could put it to see the new USB drive being automounted.

---

### Post by agillator on 2011-09-22
If you want to delete files from the destination that are not on the source, you need rsync -av --delete . . . . . Otherwise it will update files, add files that are not there, but will not delete files.

---

