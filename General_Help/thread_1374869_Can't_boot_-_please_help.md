---
title: "Can't boot - please help"
date: 2010-01-07
forum: General Help
---

### Post by gryokelbas on 2010-01-07
Hello all.

I have a problem with my ubuntu installation, if anyone could help it would be greatly appreciated.

I recently installed the newest ubuntu desktop version to my laptop (asus f3s). Everything was working great but the other day my battery ran out, it shut down and now when I try to boot it up again, it won't. I get the grub command line and I have tried many tutorials on how to boot from there but nothing have succeeded. Please advice what I should do. The grub command line gives an error no command found: 'kernel' when I try to follow a booting tutorial.

Thanks in advance!

---

### Post by gryokelbas on 2010-01-07
some more information: I installed linux into my windows partition and both should be bootable however only windows works now. After I select ubuntu, I get the grub command line.

Thanks!

---

### Post by pedro_orange on 2010-01-07
Try 

> gdm

On the command line. This will try to load the desktop manager. I suspect this won't work - but it can't hurt. Did you install with WUBI or something? I would have thought a normal installation has it's own partition.

---

### Post by MNubbe on 2010-01-07
Are you able to see the contents of grub's working folder somehow from windows, a liveCD, or otherwise (I am not familiar with wubi)?  Particularly, what is in the folder where the kernel images are (/boot for me) and what is contained in the text file menu.lst (/boot/grub for me).

---

