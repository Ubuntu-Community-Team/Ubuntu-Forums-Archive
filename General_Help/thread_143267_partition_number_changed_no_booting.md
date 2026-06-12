---
title: "partition number changed no booting"
date: 2006-03-12
forum: General Help
---

### Post by ramaswamyps on 2006-03-12
i had to delete a partition for want of space.
i deleted partition 7 whaen ubuntu installed in hda8
now ubuntu is in hda7 and i am not able to grub-install /dev/hda7
it gives error reading stage 1 
how can i recover the install.
i have edited the fstab with correct partition numbers.
any help or reinstall?

---

### Post by WakkiTabakki on 2006-03-12
I'd suggest downloading a LiveCD (600 Mb) or the linux rescue disc (125Mb) [http://www.sysresccd.org]("http://www.sysresccd.org").
Boot comp from CD, run grub and set the boot partition to the correct one, doing something like:
Start grub (as root user)
# grub
grub> root (hd0,0)                               //  Where (which drive/partition) to find  /boot/grub/  ?
grub> setup (hd0)                                //  Where (which drive) to write  MBR (master boot record) ?
grub> quit


Hope it helps
/N

---

### Post by ramaswamyps on 2006-03-12
thanks WakkiTabakki
i had got a livecd also when i bought ubuntu5.10
i used it as said in rescue mode.
well it worked nicely.
if u know the answer for the follwing please give me an idea.
i tried mounting this new ubuntu partition in pclinuxos and chrooted into ubuntu
grub-install /dev/hda7 gave error like error reading grub stage1.
but now with livecd mounting it installed ok
why why?
:KS :KS :KS

---

