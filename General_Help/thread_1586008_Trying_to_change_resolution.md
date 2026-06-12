---
title: "Trying to change resolution"
date: 2010-10-01
forum: General Help
---

### Post by Khbuex on 2010-10-01
Hi,

I have just installed Ubuntu 10.04 server on VM. Installation went well and now im trying to change the console resolution.

I have changed the grub.cfg file and added the "vga=791", but after rebooting I get a black window (on the vm), nothing written nothing is happening.

So how do I change the console resolution?

Thanks!

---

### Post by plucky on 2010-10-01
> **Khbuex said:**
> Hi,

I have just installed Ubuntu 10.04 server on VM. Installation went well and now im trying to change the console resolution.

I have changed the grub.cfg file and added the "vga=791", but after rebooting I get a black window (on the vm), nothing written nothing is happening.

So how do I change the console resolution?

Thanks!

vga=791 is deprecated in Lucid 10.04

See [Grub2 Basics](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

 Look for Grub_GFXmode to set your resolution.

Good Luck

---

### Post by Khbuex on 2010-10-01
I've changed the line to GRUB_GFXMODE=1024x768
and ran sudo update-grub.

After reboot it changed the resolution to the desired one for a second but then again went to 640x480. :(

What's next?

---

### Post by Khbuex on 2010-10-01
up up...

---

### Post by Khbuex on 2010-10-01
please, someone?

---

