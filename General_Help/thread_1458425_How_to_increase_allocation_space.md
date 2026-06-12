---
title: "How to increase allocation space?"
date: 2010-04-20
forum: General Help
---

### Post by shaquille on 2010-04-20
Hellow,
I install Ubuntu inside my Windows XP. At the time of installation I allocate 10GB space for Ubuntu. Now I need to increase the space. I have more space on the selected partition and it is an NTFS partition. 

How I can increase the space. Somebody help me.

Thanking
Shaquille

---

### Post by foxmulder881 on 2010-04-20
Use a partition manager from within Windows and change your partitions accordingly.

---

### Post by shaquille on 2010-04-20
> **foxmulder881 said:**
> Use a partition manager from within Windows and change your partitions accordingly.

I have enough space on the partition where I install Ubuntu & it is 47GB. But at the time of installation when I was prompted for space allocation for Ubuntu I chose 10GB. Now in Ubuntu I find it has 10GB Filesystem. I wanna increase the allocation space for Ubuntu, Not increasing partition space.

Thanks

---

### Post by foxmulder881 on 2010-04-20
Yeah I know what you mean. If you extend the partition in Windows, then when you boot up Ubuntu, it should detect the new size automatically.

---

### Post by garvinrick4 on 2010-04-20
You could put your Install CD in for Ubuntu, reboot and choose the Live CD not the install and when it boots up go to gparted and right click on your Ubuntu partition and go to resize or move and see if you can make it larger there.  If you used WUBI instead of a seperate partition forget all I said. I just reread and it sounds like you have 37 gig of unallocated space on the Ubuntu partition and it will
be easy to resize in gparted.

---

### Post by shaquille on 2010-04-20
thanks, I am trying it.

---

### Post by garvinrick4 on 2010-04-20
> **shaquille said:**
> thanks, I am trying it.
Did you increase the size of your partition there Shaq.

---

### Post by annemary on 2010-05-12
shaquille,

Was it successful?
If so can you elaborate the steps here?
I'm a newbie..


Thanks in advance,
Anne

---

