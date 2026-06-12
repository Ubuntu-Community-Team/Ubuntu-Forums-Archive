---
title: "Using Terminal to Browser external HDD."
date: 2011-05-07
forum: General Help
---

### Post by warrior_juggalo on 2011-05-07
I'm running Fedora 14 but thought terminal commands are much the same through all linux OS's....

I open a terminal, I type...

[mitch@mitch /]$ cd /media
[mitch@mitch media]$ ls
3c403cc9-9f0c-4035-9148-6242daf8da84  My Book
[mitch@mitch media]$ cd /media/My Book
bash: cd: /media/My: No such file or directory
[mitch@mitch media]$

So i open Partition Manager cause i remember there been another directory to it under "/dev/sdc1", Sure enough it was, So i enter....

[mitch@mitch /]$ cd /dev/sdc1
bash: cd: /dev/sdc1: Not a directory
[mitch@mitch /]$ 

What am i doing, Is The link between the linux file system and the external not seen as a directory so to speak if that makes any sense?

There's no particular reason i NEED to do this, It's justb bugging me that i can't get into it.

---

### Post by doas777 on 2011-05-07
try 
```
cd "/media/My Book"
```the space in MyBook was messing with the cd command. the double quotes compensate.

---

### Post by matt_symes on 2011-05-07
Hi

Try this

```
ls /media/My\ Book
```

or 

```
ls "/media/My Book"
```

The spaces are causing you problems and either need to be quoted or escaped.

Kind regards

---

### Post by warrior_juggalo on 2011-05-07
Thank you 10 thousand!

---

