---
title: "unable to complete the boot process even in recovery mode"
date: 2010-09-20
forum: General Help
---

### Post by droople on 2010-09-20
Hi All

I installed ubuntu 10.04 by wubi. It works perfect until I installed and ran "startupmanager".

I find that I can't enter ubuntu, even in recovery mode.

The screen keeps showing "rstslog main process ended, respawning [fail]" and other text :(

Anyone can help?

Thanks in advance.

Cheers

---

### Post by bcbc on 2010-09-20
What did you change when you ran startupmanager?

Do you see the grub menu at boot? if you hit 'e' on the first entry what does it look like?

---

### Post by droople on 2010-09-21
> **bcbc said:**
> What did you change when you ran startupmanager?

Do you see the grub menu at boot? if you hit 'e' on the first entry what does it look like?

I don't think I changed anything.

The grub entry is as follows

insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 62f4cc0df4cbe201
loopback loop- /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.32-25-generic-pae root=/dev/sda2 loop=/ubuntu/d\isks/root.disk ro 1 440 480 quite splash
initrd /boot/initrd.img-2.6.32-25-generic-pae

---

### Post by bcbc on 2010-09-21
delete everything to the right of "loop=/ubuntu/disks/root.disk ro" and CTRL+X to boot. See what happens.

Or try "ro text" to see if it will boot in text mode.

---

### Post by droople on 2010-09-21
delete everything to the right of "loop=/ubuntu/disks/root.disk ro" works 

Thank you so much. :)

Now I uninstalled the startupmanager.

---

