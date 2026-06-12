---
title: "batch text file"
date: 2006-05-03
forum: General Help
---

### Post by Manuka on 2006-05-03
Hi all,

What is the quickest and dirtiest way to batch a whole lot of text files (placed in the same directory) into ONE text file?..

In other words, text contents of each file would be copied and pasted head to tail in a batch file...

Thanks!

Manuka

---

### Post by nanotube on 2006-05-03
run command:
```
cat /where/your/files/are/located/* > /where/you/want/you/concatenated/file
```
that's it. :)

---

### Post by aysiu on 2006-05-03
Maybe [this](http://ubuntuforums.org/showthread.php?t=155641) might help.

---

### Post by IYY on 2006-05-03
[QUOTE=nanotube]run command:
```
cat /where/your/files/are/located/* > /where/you/want/you/concatenated/file
```
that's it. :)[/QUOTE]

">" overwrites. ">>" appends:

```
cat /where/your/files/are/located/* >> /where/you/want/you/concatenated/file
```

---

### Post by Manuka on 2006-05-03
[QUOTE=aysiu]Maybe [this](http://ubuntuforums.org/showthread.php?t=155641) might help.[/QUOTE]

Thanks a lot, i'm almost there now!

cat ...>... and especially cat ...>>... are great as long as I don't have to type the file names myself (long list with different names... I thought about a trick to rename all of them, eg 1.txt --> 1000.txt, but not as easy with files with very different names).

That's why your link and the idea to use ls and get all files in one line were great. HOWEVER... ls -x still gives me all files in different lines (one collumn).

Any clue?

Cheers,
Manuka

---

### Post by IYY on 2006-05-03
> cat ...>... and especially cat ...>>... are great as long as I don't have to type the file names myself (long list with different names... I thought about a trick to rename all of them, eg 1.txt --> 1000.txt, but not as easy with files with very different names).

You don't have to type the filenames. That's what the * is for: it will run the command for all files in that directory.

---

### Post by Manuka on 2006-05-03
wow... yeah... that works...
At first, I thought * meant I needed to replace it with the file name...

All is good now!

Thanks so much!

---

### Post by nanotube on 2006-05-03
heh have fun. :)
in general, if you want to get more comfortable with the commandline way of doing things, you might want to go to the first link in my sig, go to the "other commandline resources" section, and check out some of the tutorials i have listed there.

---

