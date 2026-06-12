---
title: "turning off plymouth boot screen"
date: 2010-09-23
forum: General Help
---

### Post by SimplySimon... on 2010-09-23
Hi there,

quite a while ago i decided i wanted to change my boot screen and i installed plymouth themes and used solar and now that i dont like any of the Plymouth themes, i want the original purple boot screen back but i dont know how and it would be awesome if somebody could tell me 

thanks

P.S I'm a bit of a linux noob so sorry if i got anything muddled up lol :)

---

### Post by Chris1274 on 2010-09-23
```
sudo update-alternatives --config default.plymouth
```
 
That will give you a list of the plymouth themes that you have installed. I can't remember what the default purple theme is called, but it's probably #0 on your list, so just follow the on-screen instruction to change it. Then:
 
```
sudo update-initramfs -u
```
 
Btw, if you're not happy with any of the plymouth splash screens you can always boot up in text mode.

---

### Post by SimplySimon... on 2010-09-23
Thanks i will try it now!! x]

---

### Post by SimplySimon... on 2010-09-23
No option 0 is kubuntu boot scrren but thanks anyway x]

---

