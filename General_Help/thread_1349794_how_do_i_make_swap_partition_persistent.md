---
title: "how do i make swap partition persistent"
date: 2009-12-08
forum: General Help
---

### Post by n4pgw on 2009-12-08
Ubuntu 9.10 desktop:

---

### Post by teward on 2009-12-08
what do you mean by "making the swap partition persistent"?

---

### Post by wojox on 2009-12-08
[SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by n4pgw on 2009-12-08
OOPS!!

I was looking to see if this question was in the forum, but I hit enter at the wrong time and it posted.  

My problem was that I changed swap partitions when I installed Ubuntu.  I created a partition at the end of the drive and the install created one at the end of the ubuntu partition in addition.  I deleted the automatically created one and wanted to use the one I created.  I had to edit the /etc/fstab file to reflect the partition I wanted.  

Before I made the change, Ubuntu stopped booting and would only allow recovery mode boot.  I made the change and now it boots to the proper desktop.

Sorry I posted the question, it was unintentional

Thank you very much for such a fast reply.  It is great to see help available so quickly.  

Happy Christmas! :)

Buck

---

