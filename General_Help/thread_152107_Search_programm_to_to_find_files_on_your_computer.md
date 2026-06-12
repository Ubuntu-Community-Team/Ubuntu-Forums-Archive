---
title: "Search programm to to find files on your computer"
date: 2006-03-29
forum: General Help
---

### Post by GreveFelix on 2006-03-29
Hello,
is there a search Programm to search and find files on your own computer and which one should I install.
Thanks for help!:)

---

### Post by xXx 0wn3d xXx on 2006-03-29
[QUOTE=GreveFelix]Hello,
is there a search Programm to search and find files on your own computer and which one should I install.
Thanks for help!:)[/QUOTE]
Try Beagle, it's the best search tool. Plus under Places you can search for files.

---

### Post by Sef on 2006-03-29
There is Beagle.  You can add it from the Add Applications (under Applications), via syanptic, or via the termainal.

---

### Post by Kyral on 2006-03-29
Beagle is flat out awesome. Thing is it needs the fstab to be modified to include "user_xattr" on the partitions you wanna search, but its no big deal. Also the first time you fire up the daemon (It works by indexing files and constantly checks for changes, hence why user_xattr is needed) you will notice a memory spike as it builds its index.

Locate (and its brother SLocate) are the tried adn true methods of location. However they cannot search "inside" files like Beagle can. They also use a database, but that is usually generated every night with a cronjob. 

The Deskbar Applet provides a combined interface to both. If Beagle is present it will use it Beagle, other wise it will fall back to Locate. Frankly I'd install both seeing as they have uses in different situations

---

### Post by Ramses de Norre on 2006-03-29
I've been using locate which works very good, do sudo updatedb to update the database and then locate keyword to search, you can pipe the output to grep to filter it (e.g. locate info | grep hard to search for files/folders with names including hard and info).

---

### Post by GreveFelix on 2006-03-30
Thanks for your suggestions ... I will try them

---

### Post by trent dillman on 2006-03-30
If you feel like learning the syntax, there's also my personal favorite:

find

Look it up in the man pages. There's too much for me to go into here.

---

