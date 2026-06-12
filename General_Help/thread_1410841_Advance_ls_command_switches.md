---
title: "Advance ls command switches"
date: 2010-02-19
forum: General Help
---

### Post by e24ohm on 2010-02-19
Folks:
I am having a hard time finding the answer to the following. Due to a small screen size i have the following issue.

Say for example: there is a folder with 200 items that are a mixture of folders and files. Is there a switch for 'ls' to return only results that match a specific condition? For example: I need to run 'ls -l' against a file that I know begins with 'scr';however, I can not scroll backup of the screen to review all the resualts returned.

thank you,
E

---

### Post by lloyd_b on 2010-02-19
> **e24ohm said:**
> Folks:
I am having a hard time finding the answer to the following. Due to a small screen size i have the following issue.

Say for example: there is a folder with 200 items that are a mixture of folders and files. Is there a switch for 'ls' to return only results that match a specific condition? For example: I need to run 'ls -l' against a file that I know begins with 'scr';however, I can not scroll backup of the screen to review all the resualts returned.

thank you,
E

Try ```
ls -ld scr*
```The "-d" prevents ls from recursing into subdirectories, so you only see the matching entries in the current directory, and "scr*" tells it to display only the entries that start with "scr".

Lloyd B.

Edit - If you're having problems with not being able to scroll backwards, try piping the command to "more":```
ls -l | more
```This displays the output a page at a time.

---

### Post by e24ohm on 2010-02-19
> **lloyd_b said:**
> Try ```
ls -ld scr*
```The "-d" prevents ls from recursing into subdirectories, so you only see the matching entries in the current directory, and "scr*" tells it to display only the entries that start with "scr".

Lloyd B.

Edit - If you're having problems with not being able to scroll backwards, try piping the command to "more":```
ls -l | more
```This displays the output a page at a time.

wow...this is great...thanks so much. I wish they had this in my book....

Cheers mate!!! thanks again...

---

### Post by RedSquirrel on 2010-02-19
You can also use 'less'.

This allows you to scroll backwards and forwards by pressing PageUp/PageDown when you're looking through the list of files:

```
ls -l | less
```

Press 'q' when you're done.

---

### Post by jobix on 2010-02-19
Another option is the "find" command, e.g.:

> find . -name "scr*"

find also lets you find files based on different criteria such as type, modification time, permissions, etc. You can even use it in conjuction with "-exec" to perform actions. For instance, if you want to find files that have group permissions set to "w", you can execute:

> find . -perm -g=w

Say you want to remove only those files:

> find . -perm -g=w -exec rm -i {} \;

---

### Post by blur xc on 2010-02-19
I am slightly miffed by this omission as well.  I miss dir /p from the dos days (blasphemy, I know).  piping into less or more does the job, but at the expense of color.  I don't like using less because then when you hit q it all disappears, and I don't have a photographic memory.

BM

---

### Post by Tibuda on 2010-02-19
> **blur xc said:**
> I am slightly miffed by this omission as well.  I miss dir /p from the dos days (blasphemy, I know).  piping into less or more does the job, but at the expense of color.  I don't like using less because then when you hit q it all disappears, and I don't have a photographic memory.

BM

you can use this to display colors from ls to less:
```
ls --color=always -l | less
```
the default is **--color=auto**, that does not display colors when used in a pipe.

---

### Post by blur xc on 2010-02-22
> **danielrmt said:**
> you can use this to display colors from ls to less:
```
ls --color=always -l | less
```the default is **--color=auto**, that does not display colors when used in a pipe.


That's pretty slick- added that to all my ls aliases (ll, la, lla, etc...)

Thanks!
BM

---

