---
title: "Does &quot;Swap Space&quot; exist in every installation?"
date: 2011-12-16
forum: General Help
---

### Post by newhere_m on 2011-12-16
While trying to learn about encrypting "swap space" I realized there is no swap space in my own hard disk. I have installed Ubuntu 10.04 LTS-2 and the root directory contains these subdirectories and symbolic links:

bin  boot  cdrom  dev  etc  home  initrd.img  initrd.img.old  lib  lost+found  media  mnt  opt  proc  root  sbin  selinux  srv  sys  tmp  usr  var  vmlinuz  vmlinuz.old

Am I correct to say that there is no swap space or am I unable to realize its presence?

---

### Post by snowpine on 2011-12-16
Your favorite system monitor (top, gnome-system-monitor, etc.) will tell you if you have swap space and how much you are using.

You can read more here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by 2F4U on 2011-12-16
A swap partition needs to be explicitly created. You can run without swap. You can use

sudo fdisk -l

(lower case L) to find out if there is a swap partition. Here is a sample output

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   294922239   147460096   83  Linux
/dev/sda2       294922240   312498175     8787968   82  Linux swap / Solaris

---

### Post by snowpine on 2011-12-16
> **2F4U said:**
> A swap partition needs to be explicitly created. 

Not true; the Ubuntu 10.04 installer will automatically create a swap partition unless Manual partitioning is selected.

---

