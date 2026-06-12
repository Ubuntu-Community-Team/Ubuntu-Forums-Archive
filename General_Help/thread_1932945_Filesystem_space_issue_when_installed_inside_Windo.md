---
title: "Filesystem space issue when installed inside Windows"
date: 2012-02-28
forum: General Help
---

### Post by sagardua297 on 2012-02-28
Hello All,

Ive just installed Ubuntu 11 inside my windows 7. The installation drive had 37gb free space. I installed whilst I was using WIndows.

The installation was successful, however when i open /home - it gives free space as to only 2.1GB. How can this be possible as I installed Ubuntu on a drive which had 37gb free space.

Even more confusing is when I right click on Properties under /filesystem - it gives used contents sie as 14.7 TB and free space as 2.1 GB. Again how is this possible ?

Could someone help me out here please.

Thanks.
Sagar

---

### Post by Mark Phelps on 2012-02-28
Don't use Wubi, but from what I recall, the default install chooses the minimum size needed -- which means, as in your case, you soon run out of space.

The free space on the drive doesn't matter as the Wubi install creates a single file -- and it is the available space INSIDE that file that it is measuring.

Look through the Wubi Guide below for instructions for resizing your install:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by bcbc on 2012-02-28
This might explain things: [http://askubuntu.com/questions/107470/how-can-i-check-how-much-space-there-is-left-on-wubi-versus-how-much-space-it-ta](http://askubuntu.com/questions/107470/how-can-i-check-how-much-space-there-is-left-on-wubi-versus-how-much-space-it-ta)

---

### Post by sagardua297 on 2012-02-29
Thanks a lot...i think i got your point...will try to rectify tonight.

Cheers

---

