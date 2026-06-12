---
title: "installing grub in another disc"
date: 2010-07-31
forum: General Help
---

### Post by ibrabeicker on 2010-07-31
I had ubuntu with grub2 on my external, with 2 partitions, sdc1 and sdc2

i had to install CentOS but the only 2 options when installing was "install on sda" or "don't install bootloader" and I chose don't install because I need my external to be bootable and now the grub from my external is broken, no file found.

My question is how do I install grub 2 on /dev/sdc and update it so I can boot it?

---

### Post by prodigy_ on 2010-07-31
You can [reinstall Grub2 from Ubuntu LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD).

---

### Post by ibrabeicker on 2010-07-31
ok, i did it but now when booting my external theres a black screen saying something about minimal bash and

grub>


what went wrong?

---

### Post by prodigy_ on 2010-07-31
Then use Boot Info Script from my sig and post the results here. It usually helps to troubleshoot boot issues.

---

