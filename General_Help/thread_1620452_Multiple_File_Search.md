---
title: "Multiple File Search"
date: 2010-11-13
forum: General Help
---

### Post by kanishkdudeja on 2010-11-13
hey guys..

for example we search a file for a certain keyword..

is there any application available which will enable us to search for a single keyword in all the files within the folder ?

i want to search for a keyword in about 1000 files..if i do it manually it will take loads of time..

btw the files are of type php..

---

### Post by blueridgedog on 2010-11-13
Take a look at the man page for "grep".  It will search all files specified for a word or a string.

example:

```
grep searchword /path/to/files/*
```

---

### Post by kanishkdudeja on 2010-11-17
it searches files only within that directory..i also want it to search files within subdirectories of that directory.

---

### Post by pholden on 2010-11-17
Have a look at the man page for grep for all it's options - the switch you want it **-r** ;)

---

### Post by kanishkdudeja on 2010-11-17
thanks man..:)

---

### Post by rnerwein on 2010-11-17
hi
you can expand the grep command with following options:
grep -inH 'richi' `find  -type f`
this will give you some more informations like this:

file : line (3) ......
[COLOR=Red]./bla[/COLOR]:[COLOR=Blue]3[/COLOR]:richi is a c programmer 
as you see you get the filename "bla" and the line number of that file too.
have fun
ciao

---

### Post by kanishkdudeja on 2010-11-17
thanks man..:)

---

