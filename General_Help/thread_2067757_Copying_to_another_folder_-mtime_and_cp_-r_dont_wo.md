---
title: "Copying to another folder -mtime and cp -r dont work together"
date: 2012-10-07
forum: General Help
---

### Post by mafi127 on 2012-10-07
I'm trying to get this script to work 

```
find /media/-Arhiiv-/0day* -mtime -7 -exec cp {} /home/user/Dropbox/music/ \;

```Everyting works fine but it just copy files not folders. I need that it will copy folders.

If I edit a code and add -r then it work but then the -mtime dont work. I just copy all the files what are in the folder, I dont underestand what I'm doing wrong.

```
find /media/-Arhiiv-/0day* -mtime -7 -exec cp -r {} /home/user/Dropbox/music/ \;

```any help plz ? :confused:

---

### Post by mafi127 on 2012-10-08
some1 ?

---

### Post by mafi127 on 2012-10-08
Fount out the right command. if some1 interested then

```
find /media/-Arhiiv-/0day/2012/ -type d -mtime -7 -maxdepth 2 -print -exec cp -r {} /home/user/Dropbox/music/ \;

```

;)

---

