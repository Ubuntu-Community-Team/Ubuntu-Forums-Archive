---
title: "Help with finding words in file"
date: 2011-04-28
forum: General Help
---

### Post by uncaspi on 2011-04-28
Is there a command that could be used to find word content in a file?
I.e I want to find all files containing the word 169.254.0.0 in /etc directory.
Thanks in advance.

---

### Post by Doug S on 2011-04-28
the grep command will do what you want
In a terminal window in /etc execute:
grep "169\.254\.0\.0" *
Note that "." means match any character, but "\." means "." (see the man pages for grep)
Note most files in /etc are readable by anybody, but if not in your case you might need "sudo" prefix.
If you want just the file names, then there is a switch for that. I think the -l switch will then just list the file names.
If you also want to search sub-directories, then you need to make a script (I have one I could post if needed. But maybe someone else has a better idea.)

---

### Post by sweetleaf on 2011-04-28
> **Doug S said:**
> If you also want to search sub-directories, then you need to make a script

There's a switch for that. From grep --help:

```
  -R, -r, --recursive       equivalent to --directories=recurse
```

---

### Post by Doug S on 2011-04-28
Hi,
Yes thanks. I always had troubles with recursive before, but I just tried it and it worked fine (note 1 below). So for file names only and also search sub-directories (I changed the search string just to get some actual output on my system):
grep -l -r "192\.168\.111" *
Note 1: I still have trouble with recursive if the file name is not a total wild card. i.e. this command executed from /var/www
grep -l -r "NOFOLLOW" *.htm*
where I am looking for any html or htm file with a NOFOLLOW meta tag (as an example). (note: I realize it is because the -r switch expect a directory name. I am just trying to show what I would like to do.)
Anyway, I think the original poster has what they were looking for.

---

### Post by sweetleaf on 2011-05-12
> **Doug S said:**
> I still have trouble with recursive if the file name is not a total wild card. i.e. this command executed from /var/www
```
grep -l -r "NOFOLLOW" *.htm*
```
Does this work?
```
find . -name "*.htm*" -print0 | xargs -0 grep -l NOFOLLOW
```
(Lifted from the [xargs]("https://secure.wikimedia.org/wikipedia/en/wiki/Xargs#Examples") entry on Wikipedia.)

---

