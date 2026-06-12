---
title: "command prompt appears instead of gui"
date: 2010-05-16
forum: General Help
---

### Post by rahul1975 on 2010-05-16
When i boot to ubuntu 10.04 lts. command prompt appears instead of gui interface is this a bug. I had made a new installation of ubuntu 10.04 lts 64 bit. I new to ubuntu can anybody help.:confused:

---

### Post by drs305 on 2010-05-16
rahul1975,

First, welcome to Ubuntu and the Ubuntu forums. 

We will need some more information before we can provide meaningful answers. There are several command prompts you can end up at following an unsuccessful boot.

Did you see a Grub bootloader menu when you first booted the machine? If you have another OS installed, you should have seen a menu with choices of which OS you wanted to boot.

If you didn't see a menu, try holding down the SHIFT key as the computer boots. This should reveal the GRUB 2 menu.

If you saw the menu, selected Ubuntu, and then the computer seemed to boot the selection and *then* stopped at the prompt, the problem may be related to video or some other system problem.

If you see "grub:" or "grub-rescue" it is most likely a Grub 2 bootloader problem. If you have a blinking cursor with nothing else, it is more likely Grub 2 passed the instructions on to Ubuntu and then the Ubuntu OS failed.

Also, if you saw the Grub2 menu, have you tried selecting the "Recovery Mode" option?  If so, what happened?

---

