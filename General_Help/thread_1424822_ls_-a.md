---
title: "ls -a"
date: 2010-03-08
forum: General Help
---

### Post by frncz on 2010-03-08
I recently upgraded to:
uname -a
Linux laptop 2.6.32-15-generic #22-Ubuntu SMP Tue Mar 2 02:23:29 UTC 2010 x86_64 GNU/Linux

In a terminal, the command
ls -a
gives the same output as ls. I now have to type ls -all to get the complete listing. ls -a used to work fine. I don't understand what changed?

Thanks for an explanation

Regards

---

### Post by flippo on 2010-03-08
That seems very odd, I've never heard of it.  Does your man ls reflect this change? also does "ls -A" work as expected?

---

### Post by Iowan on 2010-03-08
> **frncz said:**
> 
Linux laptop 2.6.32-15-generic #22-Ubuntu SMP Tue Mar 2 02:23:29 UTC 2010 x86_64 GNU/LinuxIs that Karmic or Lucid? (my Karmic machine is a li'l behind on updates, but is 2.6.31.19 generic).

---

### Post by frncz on 2010-03-09
This is lucid

ls -a gives a listing of files and directories including hidden folders (ones starting with .), but no permission or owner information. ls by itself is the same as ls -a but without hidden directories.ls -A g
ls -A is pretty much the same as ls -a, but seems to find a couple of extra hidden directories.

ls  -all gives all the details

Regards
Mike

---

### Post by lotharmat on 2010-03-09
> **frncz said:**
> I recently upgraded to:
uname -a
Linux laptop 2.6.32-15-generic #22-Ubuntu SMP Tue Mar 2 02:23:29 UTC 2010 x86_64 GNU/Linux

In a terminal, the command
ls -a
gives the same output as ls. I now have to type ls -all to get the complete listing. ls -a used to work fine. I don't understand what changed?

Thanks for an explanation

Regards

What you've done is typed ls -lla which is the same as ls -la, ie the (l)ong listing of (a)ll files

ls -a just gives (a)ll files

ls -lla = ls -all = ls -lal

Does this make sense?

ls -all  is basically ls with three switches the 'l' being duplicated.

---

### Post by perham on 2010-03-09
> **lotharmat said:**
> What you've done is typed ls -lla which is the same as ls -la, ie the (l)ong listing of (a)ll files

ls -a just gives (a)ll files

ls -lla = ls -all = ls -lal

Does this make sense?

ls -all  is basically ls with three switches the 'l' being duplicated.

well said. to get the details, you need ls -l and to show all files including hidden directories you need ls -a. more info is available by "man ls"

---

### Post by frncz on 2010-03-09
Yes, indeed. Thank you. I stand corrected

Regards

---

### Post by bruno9779 on 2010-03-09
indeed. Flags composed of more than one character are determined by double hyphen:

eg

```
--all (= -a in ls)
--force-architecture
etc.
```

---

