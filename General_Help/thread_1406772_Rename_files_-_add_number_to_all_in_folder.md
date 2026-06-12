---
title: "Rename files - add number to all in folder"
date: 2010-02-14
forum: General Help
---

### Post by Animortis on 2010-02-14
Hello. I'd like some help getting together a script that will add numbers to all the files in a folder.

I've ripped most of my CDs to oggs for my new pmp, but I found that the pmp doesn't like files that are numbered just as 1 and 2, as it thinks that the 2 is more than 10. It's kind of annoying.

So instead of going through all of my music folders and renaming every file by hand from 1 to 01 and from 2 to 02, I'd ask if there's a script that can be executed to add these numbers for me. It'd be even better if it only added the number to the files with only one digit.

Here's an example:

I want to rename 
9 - One Love _ People Get Ready.ogg 
to
09 - One Love _ People Get Ready.ogg

and I'd like to do it to all single-digit files lower than 10 in the folder, if possible. If not, I can isolate them by hand.

Can anyone help? Thanks.

---

### Post by lovinglinux on 2010-02-14
I recommend using [pyrenamer](apt:pyrenamer).

---

### Post by nmaster on 2010-02-14
you can get gprename from the repos.  if you use kde, there is something similar.  i think its called krename

---

### Post by Animortis on 2010-02-14
Worked perfectly. Thanks guys.

---

### Post by falconindy on 2010-02-14
The command line version:

```
rename 's/^(\d?\ )([\ -_])/0$1$2/' *.ogg
```

---

