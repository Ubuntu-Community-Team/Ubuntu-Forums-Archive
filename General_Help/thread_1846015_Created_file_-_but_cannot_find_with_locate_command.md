---
title: "Created file - but cannot find with locate command?"
date: 2011-09-18
forum: General Help
---

### Post by borderfox on 2011-09-18
I have created a file on the ubuntu desktop.  However, at the command line, if I enter the following....


locate testfile.txt OR

locate testfile


it doesn't provide the expected result (i.e. the location of the file) whereas if I try this with another file, it shows the file location.


Can anyone shed any light on this?

---

### Post by ubiquitin.jf on 2011-09-18
You need to run the command *updatedb *as root before you can find a recently created file using *locate*

---

### Post by sisco311 on 2011-09-18
locate uses a database to read the filenames. The database is updated daily by a cron job. As ubiquitin.jf pointed it out, you can manually update the database with *sudo updatedb*.

---

### Post by borderfox on 2011-09-18
@ubiquitin.jf & sisco311:  Thanks for your replies.  I carried out a manual update as suggested.  However, I still can't pull up this file.  Is there any other reason why this would happen?

---

### Post by WorMzy on 2011-09-18
> **borderfox said:**
> @ubiquitin.jf & sisco311:  Thanks for your replies.  I carried out a manual update as suggested.  However, I still can't pull up this file.  Is there any other reason why this would happen?

Yes. By default, updatedb only scans and indexes files on the root partition. Any filesystems mounted in /mount, as well as any files stored in /proc, /dev, /sys, /tmp or /var/spool, will not be scanned and subsequently won't be added to the database.

---

### Post by borderfox on 2011-09-19
> **WorMzy said:**
> Yes. By default, updatedb only scans and indexes files on the root partition. Any filesystems mounted in /mount, as well as any files stored in /proc, /dev, /sys, /tmp or /var/spool, will not be scanned and subsequently won't be added to the database.

Excelllent - thanks for your help.

---

### Post by sisco311 on 2011-09-19
You could use find to search for files. [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

Or create a local database:
```
updatedb -l 0 -o ./my-db -U /path/to/dir
locate -d ./my-db PATTERN
```

---

