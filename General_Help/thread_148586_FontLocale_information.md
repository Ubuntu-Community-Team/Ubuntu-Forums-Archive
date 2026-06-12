---
title: "Font/Locale information"
date: 2006-03-22
forum: General Help
---

### Post by cbudden on 2006-03-22
Hello. My keyboard layout is messed up.  I have isolated it to something in my home dir as if I log on as another user the problem is not there.  I also think that it could be something to do with xorg, as if I switch to a virtual terminal (ctrl-alt-f1) the problem is not there either.  What could be causing this problem?  I have tried changing my default layout to something different (en-gb to en-us) and back again but this did not help.  

Thanks

---

### Post by gos1 on 2006-03-22
do you having problems with makin @ sign etc . I had same problem too and it was fixed when played a little with xorg.conf. I deleted the last line of keyboard part.

---

### Post by cbudden on 2006-03-22
I fixed my problem by deleting .gconf and .gconfd

---

