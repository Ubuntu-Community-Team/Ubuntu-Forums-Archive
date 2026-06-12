---
title: "Need help"
date: 2010-03-31
forum: General Help
---

### Post by Jarster1 on 2010-03-31
[LEFT][SIZE=4]I have ubuntu 9.04 , When its loading on the left corner it says unclean shutdown dev/sda1..........and on the right corner it says stage 0%.This wont let me login to my desktop  I dont know what to do i a'm a begginer and i need some help,:D[/SIZE]
[/LEFT]

---

### Post by shiningpathb4me on 2010-03-31
I would boot from a LiveCD and see i could run a file system check on whatever's mounted on /dev/sda1. In the old days I'd also tell fsck to repair it. I haven't done that in years and it wasn't ubuntu. When your in the livecd you can check the man pages for fsck etc.

#man fsck

With many commands you can test them first by giving them an option to just display the results of what it would do, if you let it.

---

### Post by Jarster1 on 2010-04-01
> **Jarster1 said:**
> [LEFT][SIZE=4]I have ubuntu 9.04 , When its loading on the left corner it says unclean shutdown dev/sda1..........and on the right corner it says stage 0%.This wont let me login to my desktop  I dont know what to do i a'm a begginer and i need some help,:D[/SIZE]
[/LEFT]
[SIZE=5] I also dont care of data loss if thats the method of fixing this[/SIZE]

---

### Post by tom4everitt on 2010-04-01
Since 9.04 is getting old anyway, I would try a complete reinstallation with the latest ubuntu (9.10). Or even the 10.04 beta. 

Since you don't care about data loss, this is probably the easiest way to fix it.

---

