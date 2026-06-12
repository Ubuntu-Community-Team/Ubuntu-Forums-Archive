---
title: "Can't change the grub menu"
date: 2006-05-01
forum: General Help
---

### Post by pars on 2006-05-01
Hello, 

My boot menu does not change although
I have reedited my /boot/grub/menu.lst
to run a new kernel..

This is strange. What a missed??

Thank you very much in advance!

pars

---

### Post by duality on 2006-05-01
try "sudo update-grub"

gl

---

### Post by pars on 2006-05-01
[QUOTE=duality]try "sudo update-grub"

gl[/QUOTE]


Hello I tried it, but it didn't not change anything..

Now I tried "grub-install"

it worked.. This is the first time I needed this command.

For test, I rechanged menu.lst, rebooted and this
time it worked without grub-install. :-k 

pars

---

