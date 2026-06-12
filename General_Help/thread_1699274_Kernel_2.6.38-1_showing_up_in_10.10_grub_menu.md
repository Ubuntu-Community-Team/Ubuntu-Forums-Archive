---
title: "Kernel 2.6.38-1 showing up in 10.10 grub menu"
date: 2011-03-03
forum: General Help
---

### Post by edm1 on 2011-03-03
Last week i decided to give the 11.04 alpha 2 a go on my laptop but compiz is currently too unstable for the OS to be of any use so I reinstalled 10.10. In doing this I deleted all partitions and started completely afresh. Strangely since then I have kernel image 2.6.38-1 at the top of my grub menu but if i try to boot it i get either a single blinking cursor or a kernel freeze. I cant find any reason why 2.6.38-1 should be in grub on 10.10.

Could someone please give me a hand removing it from the config files as im not used to Grub2 and have been told i cant just directly remove it from /boot/grub/grub.cfg. Thanks.

---

### Post by edm1 on 2011-03-06
Not ideal but I solved the issue by 

```
sudo rm /boot/vmlinuz-2.6.38-1-generic /boot/initrd.img-2.6.38-1-generic
sudo update-grub
```

Why were these packages installed when they weren't even present in synaptic?

---

