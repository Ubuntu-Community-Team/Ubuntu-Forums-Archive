---
title: "Increase swap size"
date: 2011-10-22
forum: General Help
---

### Post by vat with tux on 2011-10-22
Hi friends...

I just switched to ubuntu 11.10 from 11.10.

I'm having 1 GB RAM & current swap size is 256 MB. 
Now the problem is that when I open 2-3 application together like (eclipse, nautilus, browser) then system starts hanging like a hell. When I saw system monitor i come to know that 90% swap was full. This wasn't happening in previous versions. 

So i want to increase swap size up to 512 MB so is any way to do that then please tell me...

thanking in advance....

---

### Post by Sef on 2011-10-22
Do you have any empty space after your swap?

---

### Post by scania_gti on 2011-10-22
You can remove swap at all.
When reinstaling distro from CD mark swap as ext4, and ubuntu (xubuntu) installing without swap.
My xubuntu working without swap just perfect.

---

### Post by vat with tux on 2011-10-23
I have installed ubuntu inside windows using wubi installer. I'm having around 10GB empty space in my ubuntu partition.

---

### Post by bcbc on 2011-10-23
See this: [https://wiki.ubuntu.com/WubiGuide#How_do_I_increase_my_swap_space.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_increase_my_swap_space.3F)

I also noticed 11.10 was very sluggish on my old test computer with 1GB ram. 

PS you don't want to create swap inside the ubuntu partition (virtual disk). It would be a lot slower. The guide shows how to create it on your /host partition instead

---

