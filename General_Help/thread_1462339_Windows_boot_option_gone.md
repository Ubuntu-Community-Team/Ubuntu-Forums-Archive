---
title: "Windows boot option gone?"
date: 2010-04-25
forum: General Help
---

### Post by sailor420 on 2010-04-25
Hi all,

I have an HTPC that dual boots Ubuntu 9.10 (upgraded from 9.04, so still using GRUB 1.x) and Windows (for Netflix duties). I recently rebooted the machine to watch some Netflix movies, only to discover that the GRUB menu no longer has an option to boot Windows.

I imagine that this could have happened after an apt-get upgrade installing a new kernel; it has been a while since I rebooted the machine and could have missed it.

How do I go about getting the windows boot option back into my GRUB boot list?

Thanks!

---

### Post by KeyserSoze93 on 2010-04-25
Assuming your windows partition is the first partition of the first hard drive, add the following lines to your /etc/grub/menu.lst

(modify according to your version.)

```

title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by dino99 on 2010-04-25
sudo update-grub

---

### Post by sailor420 on 2010-04-25
> **KeyserSoze93 said:**
> Assuming your windows partition is the first partition of the first hard drive, add the following lines to your /etc/grub/menu.lst

(modify according to your version.)

```

title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

Thanks, this worked perfectly. Not sure why this is happening--when I run sudo update-grub, it fails to detect the Windows partition. Any idea why it might be missing this?

---

