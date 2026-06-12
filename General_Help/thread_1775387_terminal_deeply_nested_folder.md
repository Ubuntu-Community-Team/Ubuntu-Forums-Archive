---
title: "terminal deeply nested folder"
date: 2011-06-04
forum: General Help
---

### Post by l3ecl on 2011-06-04
hi

i was wondering what's the fastest way to access a deeply nested folder.

is there a way to 'cd' to the most nested folder given that i know the folder name?

---

### Post by Lateralis on 2011-06-04
```
cd /path/to/folder
```

e.g. 

```
cd /usr/local/bin
```  

Should you wish to open up this folder in Nautilus, you can do that too!

```
nautilus /path/to/folder
```

---

### Post by matt_symes on 2011-06-04
Hi

> **l3ecl said:**
> 
i was wondering what's the fastest way to access a deeply nested folder.

Symlinks to the deeply nested directory ?

> is there a way to 'cd' to the most nested folder given that i know the folder name?Not that i'm aware of.

Kind regards

---

### Post by /Dev on 2011-06-04
> **l3ecl said:**
> hi

i was wondering what's the fastest way to access a deeply nested folder.

is there a way to 'cd' to the most nested folder given that i know the folder name?

Well the fastest way would be to type the first letter of the directory and push tab unless there are multiple folders with the same first letter in which case you would just put the second unless it matched another folders first two character's 

rinse and repeat for each folder under need the previous

so say i was trying to access a users desktop

```

cd /ho
push tab
cd /home/st
push tab
cd /home/stitch/De
tab
cd /home/stitch/Desktop/
enter

```auto complete was designed to save you enormous amounts of typing
especially when your managing files :P

btw can't believe how many people don't know about the tab autocomplete

---

### Post by DaithiF on 2011-06-05
Hi, 2 other suggestions, 
1. check out CDPATH (see man bash for details)
2. this script is useful for bookmarking often-accessed directories in the terminal: [http://www.perlmeister.com/scripts/cdbm.html](http://www.perlmeister.com/scripts/cdbm.html)

---

