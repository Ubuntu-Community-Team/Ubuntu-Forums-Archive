---
title: "Rsync: Help with text file synthax INCLUDE/EXCLUDE and OPTION"
date: 2010-01-21
forum: General Help
---

### Post by nomnex on 2010-01-21
English is not my first language. The man rsync is difficult to understand. I want to backup some folders recursively and
some files, see [1] in my /home dir to an external USB HD (Ext4). I want
to use a text file for the purpose.

[1]
/home/user/Documents
/home/user/Software

/home/user/.evolution/addressbook/local/system/addressbook.db
/home/user/.evolution/calendar/local/system/calendar.ics
/home/user/.evolution/memos/local/system/journal.ics
/home/user.evolution/tasks/local/system/tasks.ics


First (1st) attempt

[OPTION] --exclude-from=fileA

[SYNTAX] fileA

+ Documents
+ Documents/**
+ Software
+ Software/**
#
.evolution/addressbook/local/system/addressbook.db
.evolution/calendar/local/system/calendar.ics
.evolution/memos/local/system/journal.ics
.evolution/tasks/local/system/tasks.ics
#
- *

Output: Documents & Software folders: PASS. .evolution files: FAIL


Second (2nd) attempt

[OPTION] --files-from=fileB

[SYNTAX] fileB

Documents
Software
#
.evolution/addressbook/local/system/addressbook.db
.evolution/calendar/local/system/calendar.ics
.evolution/memos/local/system/journal.ics
.evolution/tasks/local/system/tasks.ics

Output: Documents & Software folders: PASS .evolution files: FAIL


QUESTIONS

What is the correct syntax of the text file
What is the correct option to use
What is the difference between --exclude-from vs include-from vs.
--files-from

I am thankful if you can provide easy to grasp examples and
explanations.

---

### Post by Lars Noodén on 2010-01-21
> **nomnex said:**
> 
What is the difference between --exclude-from vs include-from vs.
--files-from

The difference is one of exact strings versus pattern matching.  

--files-from reads the files to be rsync'd from the file you designate.  For example you could use **find** to get a list of files you want to transfer and put that list in a file 'long-list-of-files-to-transfer.txt' and then read that list with rsync:

```

rsync ... --files-from=*long-list-of-files-to-transfer.txt* ...

```

*long-list-of-files-to-transfer.txt* would include the exact name and a relevant portion of the path for each file, if not the full path.

The corresponding include option for pattern matching would be **--include=**.  Instead of reading the list of files from a file, it would use pattern matching to identify which files to transfer.

**--exclude=** uses pattern matching as well.  The analog to **--files-from** for exclusion would be  **--exclude-from=**

With **--exclude=** and **--include=** the trick, as you notice, is to have correctly formulated a pattern that matches the files you want.

---

### Post by nomnex on 2010-01-21
Thank you for the explanation. Can you help with the correct pattern?

Command:
#rsync -r -n -t -v --progress
--exclude-from=r1 /home/mt/ /home/mt/rsyncTest/

------------------------------------------

#text file <r1>:
+ .evolution/calendar/local/system/calendar.ics **(does not work)**
+ .evolution/memos/local/system/journal.ics **(does not work)**
+ .evolution/tasks/local/system/tasks.ics **(does not work)**

- *~

+ Documents/***
+ Software/***

- *

------------------------------------------

The only way to archive the ".evolution part" is to type "a line for
each folder path"

+ .evolution
+ .evolution/calendar
+ .evolution/calendar/local
+ .evolution/calendar/local/system/** **(this will work)**

**First question:** Is there a shorter syntax to get this result, and which
one?

**Second question**: If I want the .evolution files copied at the root
of /rsyncTest/, see print screen (i.e. without the folder structure) what syntax or rule do I need?

Thank you.

---

### Post by Lars Noodén on 2010-01-22
> **nomnex said:**
> 
**First question:** Is there a shorter syntax to get this result, and which one?


I would try with [b]--include=[/i] to get those.

You can increase the verbosity further by using two **-v**'s

> **nomnex said:**
> 
**Second question**: If I want the .evolution files copied at the root
of /rsyncTest/, see print screen (i.e. without the folder structure) what syntax or rule do I need?


Maybe do those separately.

---

