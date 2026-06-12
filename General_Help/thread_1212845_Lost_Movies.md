---
title: "Lost Movies"
date: 2009-07-14
forum: General Help
---

### Post by andygee on 2009-07-14
I was cleaning up my external hard drive and changed the folder name on the folder with all my movies in it now i cannot find the file at all.

i've tried the locate and find commands in terminal to no avail and ive restored everything from the trash can.

any ideas?????

---

### Post by bryncoles on 2009-07-14
what did you change the name to / from?

my first idea is stop using ur external hard drive... otherwise data recovery could become difficult!

look into this: [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

its in the repo's and has a walk through guide on the website...

---

### Post by andygee on 2009-07-14
changed folder name from movies to video for use with my ps3

---

### Post by nothingspecial on 2009-07-14
How did you change the name?

What sort of video files are they?

---

### Post by andygee on 2009-07-14
Right click> rename 

Checked out photorec but i have no idea how to use the tar.bz2 i should as ive had ubuntu since hardy hahaha

thanks for the help so far

---

### Post by stinger30au on 2009-07-14
this has happend to me before using 9.04

restart the pc and see if it has come back

also make sure oyu turn on 

show hidden files

this is found in view
put a tick in the box that says show hidden files

also do you remember did you happen to put a "." infront of what you typed?

if you rename a directory to 
.mystuff

it will turn invisible

also if you fireup shell(terminal screen) and chage directorys to the directory where you were and do a 

ls

can you see it???

---

### Post by nothingspecial on 2009-07-14
If the movies are .wmv then navigate to your external drive```


cd /media/disk
```

or whereever it is then try

```
find -name "*.wmv"
```

change .wmv to whatever extension they have.

---

### Post by nothingspecial on 2009-07-14
Sorry hit reply by mistake

If the above doesn`t work

then ```
find -mtime 0 | less
```

will find all files that have been changed/modified in the last 24 hours.

---

