---
title: "How do I clean up the GRUB boot loader?"
date: 2010-03-09
forum: General Help
---

### Post by ggabu on 2010-03-09
How do I clean up the GRUB boot loader version 1.97 Beta 4. At the moment I have the following items listed:
ubuntu, linux 2.6.31-14-generic
ubuntu, linux 2.6.31-14-generic (recovery mode)
ubuntu, linux 2.6.31-15-generic
ubuntu, linux 2.6.31-15-generic (recovery mode)
ubuntu, linux 2.6.31-16-generic
ubuntu, linux 2.6.31-16-generic (recovery mode)
ubuntu, linux 2.6.31-17-generic
ubuntu, linux 2.6.31-17-generic (recovery mode)
ubuntu, linux 2.6.31-18-generic
ubuntu, linux 2.6.31-18-generic (recovery mode)
ubuntu, linux 2.6.31-19-generic
ubuntu, linux 2.6.31-19-generic (recovery mode)
ubuntu, linux 2.6.31-20-generic
ubuntu, linux 2.6.31-14-generic (recovery mode)

And the list just gets longer with every update. Why doesn't it clean itself up and only display the latest version :(

Please can someone tell me how to do it?

---

### Post by Method X on 2010-03-09
> **ggabu said:**
> How do I clean up the GRUB boot loader version 1.97 Beta 4. At the moment I have the following items listed:
ubuntu, linux 2.6.31-14-generic
ubuntu, linux 2.6.31-14-generic (recovery mode)
ubuntu, linux 2.6.31-15-generic
ubuntu, linux 2.6.31-15-generic (recovery mode)
ubuntu, linux 2.6.31-16-generic
ubuntu, linux 2.6.31-16-generic (recovery mode)
ubuntu, linux 2.6.31-17-generic
ubuntu, linux 2.6.31-17-generic (recovery mode)
ubuntu, linux 2.6.31-18-generic
ubuntu, linux 2.6.31-18-generic (recovery mode)
ubuntu, linux 2.6.31-19-generic
ubuntu, linux 2.6.31-19-generic (recovery mode)
ubuntu, linux 2.6.31-20-generic
ubuntu, linux 2.6.31-14-generic (recovery mode)

And the list just gets longer with every update. Why doesn't it clean itself up and only display the latest version :(

Please can someone tell me how to do it?

Hi.

Just comment some kernels menuentries in crub.cfg (or menu.lst):

sudo nano /boot/grub/grub.cfg 

or

sudo nano /boot/grub/menu.lst


And comment with "#" some kernels.



Look at this topic: [http://ubuntuforums.org/showthread.php?t=1425142]("http://ubuntuforums.org/showthread.php?t=1425142")

---

### Post by sparky-steve on 2010-03-09
open synaptic, quick-search for generic, and delete (remove) the ones you do not want; I'd recommend keeping the latest 3-4 kernels. You may decide otherwise.

Note: they take up minimal space, so they do no harm to stay there.

SS

---

### Post by dgoldber on 2010-05-20
Thanks, this was very helpful.

---

