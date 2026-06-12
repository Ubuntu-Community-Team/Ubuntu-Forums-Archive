---
title: "How to check the integrity of files"
date: 2009-11-25
forum: General Help
---

### Post by viking_maniac on 2009-11-25
Most of us know about the md5sum tool to check the integrity of any file after a copy or download. On Windows I've used winmd5sum, recommended by the Ubuntu help pages, and it works nice.
 
But how about checking the integrity of many files at once; like if you have a folder with 900 files or so, for example music or photo files, that have been copied and you want to check the before and after check sums? Is this possible? It's just impractical to check each and every file.
 
Thanks!

---

### Post by Sam on 2009-11-25
If they are all in the same folder:```
md5sum *
```
Otherwise:```
find path/to/directory -type f -exec md5sum {} \;
```

---

### Post by viking_maniac on 2009-11-25
> **Sam said:**
> If they are all in the same folder:```
md5sum *
```Otherwise:```
find path/to/directory -type f -exec md5sum {} \;
```

Nice! :)

How about if there are several folders underneath the main folder that you want to check, with files in them, and you want to check all the files?

---

### Post by StuartN on 2009-11-25
> **viking_maniac said:**
> How about if there are several folders underneath the main folder that you want to check, with files in them, and you want to check all the files?

Meld is quite good, or Krusader (the synchronise option) which will allow you to take actions on matches or mismatches.

---

### Post by Sam on 2009-11-25
> **viking_maniac said:**
> How about if there are several folders underneath the main folder that you want to check, with files in them, and you want to check all the files?

That's the purpose of the second command I posted!

---

### Post by viking_maniac on 2009-11-25
> **Sam said:**
> That's the purpose of the second command I posted!

LOL! Sorry. I'm not very familiar with the Linux commands. :P

Thanks, I'll test this out later and see how it goes! :)

---

### Post by aankhr0 on 2010-01-09
Hi all!

I just copied a directory containing several folders/files in an external hard disk. Then, I ran this command on the source directory:

> **Sam said:**
> ```
find path/to/directory -type f -exec md5sum {} \;
```

It just printed the md5 of each file in the terminal. What else should be done in order to check the integrity of the files in the destination directory?

---

### Post by SecretCode on 2010-01-09
I'm sure you could do the same command on the destination directory and then use sort, diff, etc etc to compare the results. But **rsync** is capable of comparing files using MD5.

Something like this:
```
rsync /path/to/source/ /path/to/dest/ -racin
```
where -r means recursive; -a (archive) means compare (almost) all attributes of the files; -c means compare checksums using MD5; -i means itemise changes; and -n means just say what needs to be synchronised.

If you run the same command without the '-n' it would then copy over any files or attributes that need to be synchronised.

---

### Post by aankhr0 on 2010-01-09
Well, thank you very much! That was exactly what I wanted :)


*EDIT*: I should state, however, that putting the paths into quotation marks (" ") didn't work. Instead, if they contained spaces, I had to type them that way:[INDENT] /asdf/folder\ name\ with\ spaces/
[/INDENT](instead of "/asdf/folder name with spaces")

---

