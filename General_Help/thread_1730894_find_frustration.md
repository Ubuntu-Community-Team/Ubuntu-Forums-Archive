---
title: "find frustration"
date: 2011-04-16
forum: General Help
---

### Post by skytreader on 2011-04-16
Hi all. I'm trying to find a certain string in one of my files in a directory. I looked up on command line tools and it seems that "find" is the one for me.

So I try doing

```
find FirstPrograms "Hello World"
```

to say look for the string "Hello World" in all files in the folder First Programs.

However, when I press enter, all I see is a list of all the files in FirstPrograms (they are not all Hello Worlds, mind you) and then the last line says

```
find: `Hello World': No such file or directory
```

man tells me

```
find [-H] [-L] [-P] [-D debugopts] [-Olevel] [path...] [expression]
```

From the little I understand of the man pages' notation, those with dashes (-) are optional and those without are required. Anything I'm missing here?

---

### Post by TeoBigusGeekus on 2011-04-16
You're looking for grep:
```
grep "Hello World" /fullpath/FirstPrograms/*
```

---

### Post by Rushyang on 2011-04-16
Find is used to find files, Find works like this..

```
find "PATH_WHERE_TO_FIND" -name "STRING_WHAT_TO_FIND"
```Like if I'm sure I'm finding helloworld..
then..
```
 find . -name "helloworld"
```If I don't remember exact file name... then I'd use string something like..

```
 find . -name "*[Hh]ello*[Ww]orld*" 
```& If you want to list the files where your string match is found using grep..

then use **-l** option along with what TeoBigusGeekus said.. it will help you list the filenames only.

---

### Post by WorMzy on 2011-04-16
Actually, anything in square brackets ([...]) is optional.

You can use the find program if you want to, but I think that grep would be easier. (You'd probably end up using grep with find's -exec flag anyway)

```
grep -R "Hello World" FirstPrograms
```

---

### Post by skytreader on 2011-04-16
Thanks for the reply. Is there any way to make grep search recursively? That is, it searches for *everything* inside the directory, including subdirectories?

---

### Post by drs305 on 2011-04-16
Don't forget you can also do this via GUI by using the Search feature. Expand the options, where you will find an area to search for specific text within the file.

---

### Post by TeoBigusGeekus on 2011-04-16
> **skytreader said:**
> Thanks for the reply. Is there any way to make grep search recursively? That is, it searches for *everything* inside the directory, including subdirectories?

Add the -R switch, as Wormzy suggested.

---

### Post by andrew.46 on 2011-04-17
Hi skytreader,

If you are interested in an introductory page on 'find' you could do worse than have a look at the Ubuntu Community Documentation:

[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

It should furnish at least a starting point and being a wiki you can add and correct the information on the page, as I have done myself :).

Andrew

---

### Post by Leppie on 2011-04-17
use it like this:
```
grep -ilr "hello world" FirstPrograms
```
r: like wormzy said, makes the search recursive
i: makes the search case-insensitive
l: only show the actual matching results.

---

### Post by HermanAB on 2011-04-17
Howdy,

Recursive grep doesn't work correctly in a Bash shell though and pretty much everybody uses Bash shells.

Here is a workaround:
```
grep -r --include=* "hello world" .
```

---

### Post by Leppie on 2011-04-17
> **HermanAB said:**
> Howdy,

Recursive grep doesn't work correctly in a Bash shell though and pretty much everybody uses Bash shells.

the default shell in Ubuntu is dash...

---

### Post by WorMzy on 2011-04-17
> **HermanAB said:**
> Howdy,

Recursive grep doesn't work correctly in a Bash shell though and pretty much everybody uses Bash shells.

Here is a workaround:
```
grep -r --include=* "hello world" .
```

Works fine in my bash shell (I use zsh by default)

> the default shell in Ubuntu is dash... 

True-ish. If you add a user with useradd, it will have /bin/bash as it's shell by default. Predefined users, however, (such as bin, sys, www-data, nobody, etc) use /bin/sh which is a symlink to /bin/dash on Ubuntu.

---

### Post by Leppie on 2011-04-17
> **WorMzy said:**
> 
True-ish. If you add a user with useradd, it will have /bin/bash as it's shell by default. Predefined users, however, (such as bin, sys, www-data, nobody, etc) use /bin/sh which is a symlink to /bin/dash on Ubuntu.

useradd will add the user with /bin/sh (which is linked to dash) as shell, adduser will set /bin/bash as default shell.

---

### Post by WorMzy on 2011-04-17
Right you are, I knew I'd get those two commands confused eventually.

---

