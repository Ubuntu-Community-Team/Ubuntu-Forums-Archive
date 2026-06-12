---
title: "move ubuntu"
date: 2011-04-12
forum: General Help
---

### Post by noxified on 2011-04-12
How to move installed ubuntu from a 80 hdd to another 80 hdd?
(first one got bad sectors)

---

### Post by seawolf167 on 2011-04-12
Boot up off a [Clonezilla ]("http://www.clonezilla.org")cd, select the option to image to another drive, then follow the on screen prompts

---

### Post by noxified on 2011-04-12
can i do it from installed ubuntu? :D

---

### Post by lithopsian on 2011-04-12
> **noxified said:**
> can i do it from installed ubuntu? :D

No.  The partition to be cloned cannot be mounted or it will almost certainly be corrupt.

---

### Post by noxified on 2011-04-12
ah crap:(that`s sux:(
I ment copy it and paste it,to that hard drive,and rebot and use it.

---

### Post by seawolf167 on 2011-04-12
Its super easy to use Clonezilla - seriously just boot off it and follow the onscreen prompts. As said previously, you can't have the partition mounted when doing this.

Clonezilla is essentially doing a "copy & paste", it just does it a little differently than a straight *cp* command

---

