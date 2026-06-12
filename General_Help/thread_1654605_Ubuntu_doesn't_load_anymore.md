---
title: "Ubuntu doesn't load anymore"
date: 2010-12-28
forum: General Help
---

### Post by Krov on 2010-12-28
After upgrading ubuntu this OS doesn't run anymore. Like I have dual booted and I choose Ubuntu press Enter then after few seconds screen goes black and restarts PC..How can I solve this problems ? I have very important information on linux, please help me to recover ubuntu :(

---

### Post by muteXe on 2010-12-28
Are you able to boot from the live cd? If you are, I would do this and copy off all of your data first.

---

### Post by Krov on 2010-12-28
I installed ubuntu on xp with wubi.

and on windows xp 

C:\ubuntu\disks\boot\grub is empty? maybe i need to install this grub here? or try with live cd?

---

### Post by dodo3773 on 2010-12-28
> **Krov said:**
> I installed ubuntu on xp with wubi.

and on windows xp 

C:\ubuntu\disks\boot\grub is empty? maybe i need to install this grub here? or try with live cd?

The problem with wubi is that when you update the kernel or grub itself it will break your installation sometimes. Do not take this as a typical Ubuntu thing it is really more of a wubi thing. This tutorial

[http://www.omaregan.com/?p=583](http://www.omaregan.com/?p=583)

seemed to work for a few people. I hope that helps. I had a talk with a guy the other day 
about this same thing and if I had to guess I would say that it is probably a grub problem.

---

### Post by muteXe on 2010-12-30
Telling us it was a wubi install in your first post would have been useful.
Did dodo's link help?

EDIT: oops just noticed the thread is solved, so i guess the link worked :)

---

