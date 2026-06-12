---
title: "Help: how to rename file to system date in terminal"
date: 2010-11-04
forum: General Help
---

### Post by samohung390 on 2010-11-04
help, anyone can help me, is there a way in terminal to rename a file to system date?

---

### Post by papibe on 2010-11-04
Using this `` you can execute a command and then use its result in another command. The command "date" can give you several formats for the current day. To rename a file use "mv".

Example:
```
$ date
Thu Nov  4 22:27:50 CDT 2010

$ date +%F
2010-11-04

$ ls
myFile

$ mv myFile `date +%F`

$ ls
2010-11-04
```
Good Luck!

---

### Post by Barriehie on 2010-11-04
The date manpage will show you -boatloads- of date options.  I use this in my backup script:
```

rsync -av /home/barrie /media/backup/barrie-[color=red]$(date +%m%d%y)[/color]
```
which results in a folder being made on /media/backup/ named [color=red]barrie-mmddyy[/color]

HTH

---

