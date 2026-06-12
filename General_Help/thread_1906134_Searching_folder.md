---
title: "Searching folder"
date: 2012-01-08
forum: General Help
---

### Post by nos09 on 2012-01-08
Hi everybody, man its good to back !

anyway I have a little problem with my music collection.. Its big, and its messy and banshee recognises only 168 gb of data and the actual folder size is 192 gb. and i was just wondering if i can search it with a little different trick like with desplyaing all the files that are not mp3 ! you know like in reverse term.

is it even possible ?!? :confused:

if not your suggestion are always welcome :D

---

### Post by nothingspecial on 2012-01-08
Assuming your music is in your Music folder, then open a terminal and type

```
find Music -not -name *.mp3 -type f

```

---

