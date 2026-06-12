---
title: "TTY resolution."
date: 2010-05-29
forum: General Help
---

### Post by ajgreeny on 2010-05-29
I have been trying to get plymouth to show properly on my ati9200se card without any luck, but I do seem to have changed my tty resolution to a high one making the typeface shown far too small for my eyesight.

I have tried all the fixes for this that I can find, editing the /etc/default/grub file to put kernel parameters in the **GRUB_CMDLINE_LINUX=""** line and trying many different parameters, such as **vga=788** etc etc.  None of then have made any difference at all.  I do run ```
sudo update-grub
``` after each edit, just in case anyone asks.  I have also run ```
sudo update-initramfs -u
```as I thought that might make a difference, but not so.

Can anybody tell me how to get back to my older lower resolution for the cli terminals, please.  This is very frustrating for me, and I suspect it must be something very simple.

EDIT:
I should also add that the resolution of the grub menu is still as it should be, and fills the screen, it is only after going to the tty terminals that I get this smaller typeface effect, I presume from the resolution that is then running, which is a native 1280x1024, I presume.

EDIT 2:
I begin to wonder whether this is not a specific problem to the machine I am using, or whether it is related to a complete change in the OS with 10.04.  I see that all the various versions of ubuntu that I have all show this same high resolution in the ttys.  I have a partition with a new install of the minimal install version to which I have added lxde to try it out, and grub from that OS is on my second disk.  If I boot to that I still get the same problem, even from the new grub2 which is on its own disk 2 (sdb).  This all seems a bit odd to me, but perhaps it is meant to be.

---

### Post by dcstar on 2010-05-30
> **ajgreeny said:**
> I have been trying to get plymouth to show properly on my ati9200se card without any luck, but I do seem to have changed my tty resolution to a high one making the typeface shown far too small for my eyesight.

I have tried all the fixes for this that I can find, editing the /etc/default/grub file to put kernel parameters in the **GRUB_CMDLINE_LINUX=""** line and trying many different parameters, such as **vga=788** etc etc.  None of then have made any difference at all.  I do run ```
sudo update-grub
``` after each edit, just in case anyone asks.  I have also run ```
sudo update-initramfs -u
```as I thought that might make a difference, but not so.

Can anybody tell me how to get back to my older lower resolution for the cli terminals, please.  This is very frustrating for me, and I suspect it must be something very simple.

I got tired of playing with Grub2 on this issue, I installed **burg** yesterday and things are much better.

---

