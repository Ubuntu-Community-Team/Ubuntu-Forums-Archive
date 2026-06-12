---
title: "Can't Backup Computer"
date: 2011-05-16
forum: General Help
---

### Post by xTLx on 2011-05-16
Okay this is driving me crazy. I just took my 1 terabyte hard drive and created two partitions on it. One I formatted for windows and the other I formatted for Ubuntu so that I could backup the contents of my hard drive for both operating systems. My computer can boot both of these operating systems so you might understand why this is useful.

HOWEVER now when I try to backup my computer using the Windows backup utility it gives me the following error: "The system cannot find the file specified. (0x80070002)"

I've looked for solutions online and tried several of them to no avail.

Any ideas of what to do?

---

### Post by wannabegeek on 2011-05-16
I don't know too much about this issue in particular, but I do know that windows has a command line
program similar to rsync called  xcopy.   I am guessing that the program you are using is looking for a particular location to back up to and doesn't see it. 

More details will help.
wbg

---

### Post by Quackers on 2011-05-16
You could try clonezilla
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by seawolf167 on 2011-05-16
> **Quackers said:**
> You could try clonezilla
[http://clonezilla.org/](http://clonezilla.org/)

Big +1 for Clonezilla.

Here is the [KB article ]("http://support.microsoft.com/kb/979281/en-us")for the error you mentioned

---

### Post by Duncan Williams on 2011-05-16
use free easus todo backup, can clone partitions, drive.
also other free software for backup/partition management.
[http://www.todo-backup.com/](http://www.todo-backup.com/)

---

### Post by xTLx on 2011-05-17
I made a compromise between installing software to use and fixing the error, so for now I'm trying out Sync Toy (by microsoft) until i can fix the error. I tried the solutions listed in the article, but none of them worked of them worked so maybe registry issues? I dunno.

Anyways Sync Toy seems like a simple enough tool to use, but im open to suggestions.

---

