---
title: "Install Ubuntu using Wubi in Windows 7 = Trashed boot loader"
date: 2010-08-14
forum: General Help
---

### Post by xissburg on 2010-08-14
Hey. So, I installed Ubuntu using Wubi in Windows 7 and it worked fine for the first few boots. I suspect that, after installing the bunch of Ubuntu updates, my boot loader was trashed. Now when I turn on the PC, I get:

error: no such device <hex numbers>
grub rescue>

And there's almost no commands which work in this command line. I got ls to work, it prints (hd0)(fd0), which I have no idea what it means.

Anyway, I want my Windows 7 back as fast as possible, I'm really frustrated. Any ideas about what I can do?? I already searched a lot of stuff around the net, asked for help at #ubuntu but till now, I already wasted more than 10 hours on this without any success.

Any help is appreciated, thanks in advance.

---

### Post by bcbc on 2010-08-14
> **xissburg said:**
> Hey. So, I installed Ubuntu using Wubi in Windows 7 and it worked fine for the first few boots. I suspect that, after installing the bunch of Ubuntu updates, my boot loader was trashed. Now when I turn on the PC, I get:

error: no such device <hex numbers>
grub rescue>

And there's almost no commands which work in this command line. I got ls to work, it prints (hd0)(fd0), which I have no idea what it means.

Anyway, I want my Windows 7 back as fast as possible, I'm really frustrated. Any ideas about what I can do?? I already searched a lot of stuff around the net, asked for help at #ubuntu but till now, I already wasted more than 10 hours on this without any success.

Any help is appreciated, thanks in advance.

You need to reinstall the windows boot loader to your drive. Here's the how to (scroll to section "How to restore vista/7 bootloader") [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Alternatively, you can fix from a live CD using lilo:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
You will see some warnings which you can safely ignore. This assumes you boot from /dev/sda (most common).

---

### Post by xissburg on 2010-08-18
Thanks for the reply. Just to update my status I got to boot in Windows 7 again using the Windows 7 Recovery disc. But now I can't boot in Windows XP nor Ubuntu (installed through Wubi). [bcbc]("https://launchpad.net/%7Ebcbc") told me to start a thread here and post the results of running boot_info_script so that someone would try to help me get the other OSes booting again.This new thread is [here]("http://ubuntuforums.org/showthread.php?p=9735896").

---

