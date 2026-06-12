---
title: "Gparted Question"
date: 2010-11-14
forum: General Help
---

### Post by Tourdog on 2010-11-14
Looking at the screen shot "/dev/sda5" can be expanded into the "unallocated" to its left, correct? But, clicking "free space up/dn " seems to shrink it regardless........... what? sda5 is not mounted.

I'm missing some things here???

Any help is appreciated!

---

### Post by drs305 on 2010-11-14
The screen shot didn't attach, but since you are talking about sda5 and left free space, you are probably trying to add space outside the extended (light blue border) partition. The free space must be within the extended partition before you can add it to sda5. 

You would have to first expand the extended partition itself, then expand sda5.

---

### Post by Tourdog on 2010-11-14
drs305,     you've done an amazing job answering my question.   Thank you!

---

### Post by Tourdog on 2010-11-14
[ATTACH]175635[/ATTACH]        Another try .....



looks like one can't do it on an "edit" either.

---

### Post by Verbeck on 2010-11-14
try uploading it to an image host if you're having problems attaching it

[http://imageshack.us/](http://imageshack.us/)
[http://tinypic.com/](http://tinypic.com/)

---

### Post by Tourdog on 2010-11-14
see if this works?

---

