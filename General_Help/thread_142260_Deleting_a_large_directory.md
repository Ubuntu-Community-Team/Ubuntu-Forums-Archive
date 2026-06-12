---
title: "Deleting a large directory"
date: 2006-03-10
forum: General Help
---

### Post by Burgresso on 2006-03-10
I have a large directory of variuos files and other directories, all have permissions set so I can't erase them without going through every directory and changing the permissions of each file in them.

Is there  a short cut to do this, via the commmandline or other way?

thank a million,
burgresso

---

### Post by Sendervictorius on 2006-03-10
on commandline type:

sudo rm -rf <directoryname>
password:

the -r does a recursive removal of files and directories. The f option stops asking for confirmation on each deletion. Use sudo to execute the command as "root" to avoid permission issues.

And be careful with what you type, otherwise you may delete something unintended.

On the command line type: 
man rm
to  learn what the rm command can do for you!

---

### Post by dcstar on 2006-03-10
[QUOTE=Burgresso]I have a large directory of variuos files and other directories, all have permissions set so I can't erase them without going through every directory and changing the permissions of each file in them.

Is there  a short cut to do this, via the commmandline or other way?

thank a million,
burgresso[/QUOTE]
gksudo "nautilus --browser %U"

and then you will have root access in a Nautilus window.

---

### Post by Burgresso on 2006-03-10
Thanks guys, I appreciate it. Very helpful! \\:D/

---

