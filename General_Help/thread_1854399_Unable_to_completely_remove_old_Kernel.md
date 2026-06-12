---
title: "Unable to completely remove old Kernel"
date: 2011-10-04
forum: General Help
---

### Post by fantab on 2011-10-04
Recently the Linux kernel was updated to **3.0.0-12** from **3.0.0-11**. I removed the old Linux Kernel **3.0.0-11**-generic using Synaptic. I then *sudo update-grub*... but the old linux kernel is being listed in the terminal:

[QUOTE=from TERMINAL]Generating grub.cfg ...
Found background image: Gnome_Dark_Wood.jpg
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
[B]Found linux image: /boot/vmlinuz-3.0.0-11-generic
Found initrd image: /boot/initrd.img-3.0.0-11-generic[/B]
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Fedora release 15 (Lovelock) on /dev/sda5
done[/QUOTE]The Grub Menu at boot also lists 'Previous Versions' and also in /boot all the files from previous kernel are listed. *Please see the attached image.*

Please help me resolve this so I should only have the latest kernel everywhere.
Also, How can I prevent **memtest** from showing in the Grub Menu?

---

### Post by dino99 on 2011-10-04
its a good idea to can choose between the latest kernel and the previous good one in case of failure. That said, to remove a kernel, you have to remove the 2 related headers & the image each time (1 kernel = 3 packages).
Can be done with: sudo synaptic

---

### Post by fantab on 2011-10-04
> **dino99 said:**
> its a good idea to can choose between the latest kernel and the previous good one in case of failure. That said, **to remove a kernel, you have to remove the 2 related headers & the image each time (1 kernel = 3 packages).**
Can be done with: sudo synaptic

I have done that already... I removed everything that read 3.0.0-11 (3 packages) from Synaptic.

---

### Post by philinux on 2011-10-04
> **fantab said:**
> I have done that already... I removed everything that read 3.0.0-11 (3 packages) from Synaptic.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

Scroll down for the full command at step 5. Dry run is recommended first.

Memtest.
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId49740](http://www.dedoimedo.com/computers/grub-2.html#mozTocId49740)

---

### Post by fantab on 2011-10-04
> **philinux said:**
> [http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

Scroll down for the full command at step 5. Dry run is recommended first.

Memtest.
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId49740](http://www.dedoimedo.com/computers/grub-2.html#mozTocId49740)

**Thanks philinux**, not just for solving my issues above but for introducing me to wonderful links.

However in the memtest link the command line is incomplete:

incomplete: sudo chmod -x 20_memtest86+

```
complete: sudo chmod -x /etc/grub.d/20_memtest86+

```

---

### Post by philinux on 2011-10-04
> **fantab said:**
> **Thanks philinux**, not just for solving my issues above but for introducing me to wonderful links.

However in the memtest link the command line is incomplete:

incomplete: sudo chmod -x 20_memtest86+

```
complete: sudo chmod -x /etc/grub.d/20_memtest86+

```

Nice one.

My guess on the "error" is that the writer had used cd and was in the /etc/grub.d folder.

---

