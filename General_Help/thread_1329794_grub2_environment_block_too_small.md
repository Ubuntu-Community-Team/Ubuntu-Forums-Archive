---
title: "grub2 environment block too small"
date: 2009-11-17
forum: General Help
---

### Post by djk44883 on 2009-11-17
I'm another one with hassles with grub2

In the end - I reinstalled grub2 via live cd.  It booted and ran update-grub, no problems.  Wanted to get a clean start so I checked to reinstall grub-pc and grub-common from synaptic.  Looked good, rebooted into win xp.  When I rebooted can choose ubuntu I get -
    error: grub2 environment block too small 
    press any key to continue 
which brings me back to grub boot menu.  I can find virtually nothing about this.  

Can anyone offer me a clue?  

DJ

---

### Post by djk44883 on 2009-11-18
Still haven't found an answer about 'environment block too small' but as for a temp work around.  I added this to /etc/grub.d/40_custom

menuentry "Ubuntu"	{
set root=(hd0,5)
	linux	/vmlinuz root=/dev/sda5 ro
	initrd	/initrd.img
	}

then run sudo update-grub  Now I can boot into ubuntu, but this didn't truly fix my problem.

---

### Post by marltu on 2010-01-18
Try 
sudo rm -rf /boot/grub/grubenv
sudo grub-editenv /boot/grub/grubenv create

Somehow it worked for me. Weird bug.

---

