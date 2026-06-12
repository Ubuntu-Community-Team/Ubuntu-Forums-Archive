---
title: "Exclude backups from backup"
date: 2009-08-31
forum: General Help
---

### Post by dragos2 on 2009-08-31
I have this script that makes a backup once a day, but in the /samba folder there
is a directory named backup where the backups are stored by this script and
I don't want every backup in a new one. I used the -x switch but it does not
work, when I check my backups they include the /samba/backup files from
the previous day. 

```

NOW=$(date +"%b-%d-%y")
zip -r /samba/backup/$NOW /samba/* -x \samba\backup\*

```

How to fix this please ?

---

### Post by dragos2 on 2009-08-31
Bump.

---

### Post by DaithiF on 2009-08-31
try:
```
zip -r /samba/backup/$NOW /samba/* -x /samba/backup/\*
```

the path separator for the exclude parameter is still '/'.  The zip documentation shows examples of '\*.c', etc, but the backslash in these cases is to escape the '*' wildcard character to prevent your shell from expanding it before passing it to the zip program.  When you are specifying a path and *then* a wildcard, you use normal path separators '/' for the path, and then just a single backslash, as above.

---

### Post by dragos2 on 2009-09-01
> **DaithiF said:**
> try:
```
zip -r /samba/backup/$NOW /samba/* -x /samba/backup/\*
```the path separator for the exclude parameter is still '/'.  The zip documentation shows examples of '\*.c', etc, but the backslash in these cases is to escape the '*' wildcard character to prevent your shell from expanding it before passing it to the zip program.  When you are specifying a path and *then* a wildcard, you use normal path separators '/' for the path, and then just a single backslash, as above.

Still not working. This is weird. It still includes the previous backups.

I used your suggestion:

```

NOW=$(date +"%b-%d-%y")
zip -r /samba/backup/$NOW /samba/* -x \samba\backup/\*

```

---

### Post by DaithiF on 2009-09-01
> I used your suggestion:
```
zip -r /samba/backup/$NOW /samba/* -x \samba\backup/\*
```
thats not what i wrote though :)

```
zip -r /samba/backup/$NOW /samba/* -x /samba/backup/\*
```
be careful with the direction of the slashes -- they are all forward-slashes except for the last one

---

### Post by amac777 on 2009-09-01
From what you said you tried, you put some slashes in the wrong direction, I think you should try this:

```
NOW=$(date +"%b-%d-%y")
zip -r /samba/backup/$NOW /samba/* -x /samba/backup/\*
```

---

### Post by dragos2 on 2009-09-02
> **DaithiF said:**
> ```
zip -r /samba/backup/$NOW /samba/* -x \samba\backup/\*
```thats not what i wrote though :)

```
zip -r /samba/backup/$NOW /samba/* -x /samba/backup/\*
```be careful with the direction of the slashes -- they are all forward-slashes except for the last one

It is working, my mistake.

Thank you :)

---

