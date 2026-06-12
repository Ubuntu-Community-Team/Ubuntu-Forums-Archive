---
title: "Can't boot Ubuntu"
date: 2010-02-27
forum: General Help
---

### Post by belitos on 2010-02-27
Hello,

I have a little problem here. i have Windows Vista and i just installed the Ubuntu linux. but when i turn on my computer there is no Grub or something like Grub to chose witch OS i want to boot. my pc boot Vista automaticly. how can i restore/fix the boot manage? 

Thanks in advance.

---

### Post by ercferret18 on 2010-02-27
start a live cd, and then mount your ubuntu filesystem.

then run this: "sudo chroot <your filesystem mountpoint>"

then run this: "grub-install /dev/sda"

---

### Post by 73ckn797 on 2010-02-27
Did you install in Windows, via WUBI, or on a separate partition/drive?

---

### Post by belitos on 2010-02-28
Im kinda newb with linux..
i had this windows here for like 1 year, and i installed ubuntu yestarday.
they are in the same HD but in diferent partitions

---

### Post by jhoney142 on 2010-03-04
Hi,
 go to the BIAS and change the boot operations

---

