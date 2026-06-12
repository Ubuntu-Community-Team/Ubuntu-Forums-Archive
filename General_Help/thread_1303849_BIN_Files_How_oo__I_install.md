---
title: "BIN Files? How oo  I install?"
date: 2009-10-28
forum: General Help
---

### Post by daldude on 2009-10-28
I downloaded a supposed program for Linux which has a bin extension so I assume it's called a BIN file.

How do I install this program if it is a program in Ubuntu?


Thanks:)

---

### Post by phillw on 2009-10-28
what program ?  pop it's name on. normal downloads (packages) aren't bin files.

Phill.

---

### Post by Anonymousable on 2009-10-28
Open a terminal (Applications>Accessories>Terminal) then use 'cd' to get to the folder where you stored it, e.g.
```
 cd /home/me/Downloads
```
Then use chmod to make it executable:
```
chmod u+x [file].bin
```
Then run it:
```
./[file].bin
```

This is the usual way, but does depend on what program you're using.
Google Earth is installable like this, and I think Skype is too.
These instructions *should* apply to whatever you're using too.

---

### Post by DGortze380 on 2009-10-28
> **daldude said:**
> I downloaded a supposed program for Linux which has a bin extension so I assume it's called a BIN file.

How do I install this program if it is a program in Ubuntu?


Thanks:)

BIN is a binary file, should just run.

cd to the directory containing the file

./myFile.bin

Programs of this nature are typically placed in /usr/bin

---

### Post by Bonster on 2009-10-28
right click on it > properties > permission > check allow execute

---

