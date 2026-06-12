---
title: "Mysterious files created by root"
date: 2009-09-01
forum: General Help
---

### Post by viking_maniac on 2009-09-01
Suddenly I can see empty (text)files in almost every folder one lever from / named *

Just a *

Does anyone have a clue about what this is?

---

### Post by DaithiF on 2009-09-01
you see them where -- in the terminal ?  or in nautilus ?

can you post the output of
```
ls -la 
```
in one of the affected directories

---

### Post by viking_maniac on 2009-09-01
It really doesn't mater how I read the directories, the file is there and I'm currious about what it is and why root made them in all the folders one lever from root.

Here's the outcome from your request:

```
/mnt$ ls -la
total 8
drwxr-xr-x  2 root root 4096 2009-08-31 14:37 .
drwxr-xr-x 22 root root 4096 2009-09-01 10:23 ..
-rw-r--r--  1 root root    0 2009-08-31 14:37 *
```It's the last one, as you can see. They're all empty and their name is [COLOR=DarkRed]*[/COLOR]

---

### Post by amauk on 2009-09-01
most likely it's a typo in a command
someone wanted to glob all files, but got it wrong

this will search for all empty files, named "*", and delete them
(nb: note the backslash before the asterisk, this is very important, as this searches for a literal *, and not "all files")

```
sudo find / -type f -size 0 -name '\*' -exec rm {} \;
```

---

### Post by viking_maniac on 2009-09-01
That's my suspicion too.

Actually, I remember that I did some searching yesterday approximately when the files where created. I tried to search for some text within files and made a shell script searching with the [COLOR=Red]grep[/COLOR] string trough all folders on /. I also used a combo of several commands which I found on web in the same script afterward:

```
$ sudo find /folder/ -type f -print0 | xargs -0 grep -ils <text>
```But how that could make these files I don't know.

---

