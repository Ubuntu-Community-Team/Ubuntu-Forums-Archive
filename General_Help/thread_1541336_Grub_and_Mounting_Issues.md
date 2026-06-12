---
title: "Grub and Mounting Issues"
date: 2010-07-29
forum: General Help
---

### Post by Stupid_newbie on 2010-07-29
Hello all, I am having two minor issues and I cant figure out how to fix them.

1st issue, My grub menu is huge, every time I upgrade my Ubuntu to a higher distribution, it keeps my old one in the menu list, and then duplicates my Windows selection. I looked online to figure this out and a bunch of "how-to's" tell me to edit my "/boot/grub/menu.lst" unfortunately I don't have that file on my system. I just want my menu to hold 3 entries 

2nd issue, It keeps trying to mount my CD-rom as it boots up, it tells me "Error mounting CD Press S to continue or m to manually mount" or something like that. I'm pretty sure my CD-rom has died on me (renovations and computers don't get along btw) is there a way I can avoid this msg?

Seems like a pretty simple problem but, as you can see the alias I have, I am lost...falling asleep in Linux class in college = BAD IDEA

Running 
Lucid 10.04
Kernel 2.6.32-24 (just in case that helps)
Thanks in advance

---

### Post by Jahid65 on 2010-07-29
Solution of the 1st problem is open synaptic & search "linux-image"(without the quote). Find linux-image-2.6.32-22-generic(it is a kernel version)(may be different in your case) and so on. just remove that. Then you are OK. Please keep at least 2 kernels in grub menu. in your case boot with 2.6.32-24 kernel & do what stated above. 

second problem I don't know.

---

### Post by Stupid_newbie on 2010-07-29
I tried your suggestion, I haven't re-booted yet to find out, but Thanks in advance I'm pretty confident it will work!

---

