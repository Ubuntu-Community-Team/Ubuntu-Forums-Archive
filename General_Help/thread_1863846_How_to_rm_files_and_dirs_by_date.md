---
title: "How to rm files and dirs by date"
date: 2011-10-18
forum: General Help
---

### Post by jr223 on 2011-10-18
Hi all,

A quick question.
I have a HUGE amount of files and files in directories.
The ones I want to keep are dated July 2011 and on.
The others older then this month I want to recesivley remove.

I tried the following, but didn't see any changes to the mass amount's of files and directories.
What am I missing?

Code:
find . -type d -mtime +107 -exec rm -R {} \;

Thanks
:p

---

### Post by mikejonesey on 2011-10-18
if directorys contain files they can't be deleted... (unless you use the force option...), as your search only deletes directorys and is not forced it does nothing, add verbose option to see exactyly what it's doing :)

---

### Post by matt_symes on 2011-10-18
Hi

Try it on the files. The directories may have been modified later.

```
find . -type f -mtime +107 -exec rm -R {} \;
```

I would do this first to make sure it's the correct files you are deleting.

```
find . -type f -mtime +107 -exec echo {} \;
```

Kind regards

---

### Post by jr223 on 2011-10-18
Thanks so much will try it out and let you know.

---

### Post by mikejonesey on 2011-10-18
> **matt_symes said:**
> Hi

Try it on the files. The directories may have been modified later.

```
find . -type f -mtime +107 -exec rm -R {} \;
```I would do this first to make sure it's the correct files you are deleting.

```
find . -type f -mtime +107 -exec echo {} \;
```Kind regards

```

find . -type f -mtime +107
find . -type f -mtime +107 -exec echo '{}' \;

```

lol :P

---

### Post by matt_symes on 2011-10-18
Hi

> **mikejonesey said:**
> ```

find . -type f -mtime +107
find . -type f -mtime +107 -exec echo '{}' \;

```lol :P

Clever clogs ;) :D

Kind regards

---

