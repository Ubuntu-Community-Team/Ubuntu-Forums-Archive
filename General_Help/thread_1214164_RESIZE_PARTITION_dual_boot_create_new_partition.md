---
title: "RESIZE PARTITION dual boot create new partition"
date: 2009-07-15
forum: General Help
---

### Post by nacho32 on 2009-07-15
ok here's what I want to do I have a dual boot xp/ubuntu 904 2 IDE hard drives XP on first ubuntu on the second. Every thing works fine. I want to re size the 2 hd ubuntu and add a nts partition to it so I can use it for a temp for my TV tunner card when I use XP. Can I resize it and a new partition without hurting my ubuntu OS ?

---

### Post by TeoBigusGeekus on 2009-07-15
In small words, yes.
Boot up with the live CD, open partition manager and do it.

---

### Post by michy99 on 2009-07-15
As long as you have enough free space, it should not be a problem. Take the space off the end of the Ubuntu partition, not the front.

---

### Post by nacho32 on 2009-07-15
ok  I used the gparted live cd and all went well :) i just shrunk the 2 hd ext3 to 25 gigs gave me 49 gigs of unallocated and created ntfs primary on that unallocated , now I can use that second HD for my tv tunner card when recording live in windows to be hick up free and use it as the temp for my 1click copy, and hell I will also use it for my page-file system for xp,, happy happy joy joy :p

---

