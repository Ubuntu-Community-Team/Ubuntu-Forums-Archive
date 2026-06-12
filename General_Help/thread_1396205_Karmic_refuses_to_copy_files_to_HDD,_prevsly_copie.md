---
title: "Karmic refuses to copy files to HDD, prevsly copied by hardy"
date: 2010-02-01
forum: General Help
---

### Post by maramot on 2010-02-01
Not too long ago, I backed up a bunch of files from my laptop to an external hdd. I wanted to make a backup in case I mess something up while upgrading from hardy to karmic. Now I am trying to return the backed up files to my laptop's hard drive, before turning the external hdd back to its owner :)

The first problem I ran into was when I tried to access the backups by the graphical nautilus: the directories and files were simply not displayed. That struck me as strange, since I could see them and read/write to them while under windows xp. I tried to *ls* the contents of my main backup directory via terminal and the *ls* command was listing some of them, but not all of the files which I can see under windows.

On copying attempt (by terminal commands), I get the following error message for some of the files:

```
cp: cannot stat `*name-of-file.extension*': Input/output error
```

Any idea what could be wrong and how to fix? I am sure I can access and edit all the files from windows.

---

### Post by quixote on 2010-02-03
What is the format of the HDD?  NTFS?  what kind of Windows are you using?  If win7, it's not as lax about permissions as XP, so maybe that's messing something up.

Try running the commands as sudo, since that will show all files, including those not owned by your regular login user. In a directory where you can see some but not all of the files using plain ls, try the following: ```
sudo ls -al
``` -a means show hidden files, -l mean long form, ie show permissions, owner and group.  Is there any pattern to the permissions or ownership of the files you can vs. the ones you can't see?  Or do you still see only a subset, even when you use sudo?

---

