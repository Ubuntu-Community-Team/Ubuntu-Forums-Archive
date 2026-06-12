---
title: "DVD problem"
date: 2010-05-06
forum: General Help
---

### Post by svillega on 2010-05-06
hi 

this is my first problem since i use ubuntu the problem is:

ubuntu doesnt mount any DVD and it recognize all the dvds as blank, i believe its a problem of drivers but im not sure , besides i tried medibuntu and a lot of things that the people asks here in the forums

thanks ..

(so sorry for my bad english)

thanks again

---

### Post by jbrown96 on 2010-05-06
Try the following ```
mkdir /Desktop/DVD
``````
sudo mount -t iso9660 /dev/dvd Desktop/DVD -o loop
``` does that work?

---

### Post by svillega on 2010-05-06
thanks for replying
and ..
nop T_T 

/dev/sr0: no medium found

---

