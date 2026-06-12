---
title: "want a good replacement for 'ls | less'"
date: 2006-06-17
forum: General Help
---

### Post by xenblend on 2006-06-17
Hey all,

I do a lot of 'ls' commands and I pipe them through 'less' or 'cat' a lot. I was wondering, is there any way to preserve the color-coding that bash does with 'ls' in the 'less' command so that directories stills how up as blue, sym links as green, etc.  I've found all the files that are used to edit the 'ls' util as well as 'less' but I cant make less work without removing color-coding... :(

---

### Post by xenblend on 2006-06-17
In case anyone is interested the answer is 'ls -Al | less -R' to make less print colors.

---

### Post by caldevil on 2006-06-17
Its not working for me.

---

### Post by gorilla on 2006-06-17
ls -l --color | less -R works for me

---

### Post by 23meg on 2006-06-17
You can [set an alias]("http://ubuntuforums.org/showthread.php?t=161312") for ```
ls -l --color | less -R
``` to make things even easier. In my setup "lsc" is the alias for it.

---

### Post by xenblend on 2006-06-17
Sorry,

It's actually 'ls -Al --color | less -R'

XB

---

