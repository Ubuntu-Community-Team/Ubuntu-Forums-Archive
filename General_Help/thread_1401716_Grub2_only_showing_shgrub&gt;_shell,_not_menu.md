---
title: "Grub2 only showing sh:grub&gt; shell, not menu"
date: 2010-02-08
forum: General Help
---

### Post by contecarli on 2010-02-08
Hi,

Two days ago, I restarted my Ubuntu 9.10 Server after performing some updates. After that, Ubuntu didn't boot anymore. The Grub Loader (0.96) just said "Loading ..." and nothing else happend. I searched the net for a solution and found different ways to recover grub, but all of them faild due to my RAID 1 not being able to be mounted. Through the console on the Ubuntu 9.10 Server installation CD, I tried to reinstall GRUB, but nothing I tried worked.

Finally today, after trying the same commands multiple times, I managed to install grub2 (Grub2 v1.97~beta4) and my server finally booted again. Grub loaded and I was offered a grub shell (sh:grub> ) and after some time, I found a way to boot back into Ubuntu (Thanks to this forum!). The server still works fine and all my files are still there. (which I couldn't access before due to my home directory being encrypted)

My only problem now is, that the system doesn't start up automatically anymore. When I restart the server, I always come back to the Grub shell and have to enter the same commands over and over again. I've never seen the grub menu. The grub.cfg (which is located in /boot/grub/grub.cfg) contains all the available kernels (normal and recovery mode) and the memtest. I've also updated the grub.cfg with update-grub and update-grub2 and also disabled the GRUB_HIDDEN_TIMEOUT option (and set GRUB_HIDDEN_TIMEOUT_QUIET=false), but nothing helped. I haven't changed any other default grub2 settings, but still only see the grub shell.

Most problems I found up until now had to do with a Windows installation, but I only have Ubuntu installed on this machine.

How can I solve this problem and get grub to boot the server automatically.

Thanks in advance!

contecarli

---

### Post by Leppie on 2010-02-08
try preloading the raid module. open your grub defaults file:
```
gksudo gedit /etc/default/grub
```add the following line at the end:
```
GRUB_PRELOAD_MODULES="raid"
```save and exit the file.
re-install grub and regenerate the grub.cfg file:
```
sudo update-grub
sudo grub-install --recheck /dev/sda
```

---

### Post by contecarli on 2010-02-08
Thank you, thank you, thank you!!

Everythings working again, the grub menu is being displayed and the server starts automatically.

Thank you very much.

---

### Post by Leppie on 2010-02-08
you're very welcome. glad all is working properly now ;)

if this issue is resolved, please use the thread tools to set it to solved.

---

