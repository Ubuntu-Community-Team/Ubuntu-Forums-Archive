---
title: "Linux partition with Grub corrupted, on dual boot, what next?"
date: 2010-11-08
forum: General Help
---

### Post by vladutzzzz on 2010-11-08
Hi!
I have a dual boot drive, one is WinXp the other Ubuntu 10.04.
I don't know why, but my ubuntu partition became corrupted (booting from live cd and inputing fdisk -l in the terminal, shoes my partition as unknown type)
My Grub was on this partition, and therefore I cannot boot neither one of my two OSs.
I would like to recover my linux partition, I figure I can do that only from my WinXp partition, but I don't know where and how to install Grub.
Also, If anyone knows how I could recover from the live CD without booting Windows, please speak up, that would make everything much easier.
Another thing, it would be just super if I could recover my whole partition, not just the data, because I would hate to reinstall all the stuff that I had on my Ubuntu.
Please let me know if anyone has a solution, to any of my problems.
Thanks.

Vlad.

---

### Post by TeoBigusGeekus on 2010-11-08
Boot up with a live cd and try
```
sudo fsck /dev/sda2
```
Replace /dev/sda2 with your ubuntu partition.

---

