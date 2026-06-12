---
title: "address space collision"
date: 2011-02-25
forum: General Help
---

### Post by byammanuru on 2011-02-25
> [QUOTE][/QUOTE]Hi,

I tried to compile a Linux kernel. I downloaded the 2.6.37.2 version. And used the following commands:

```

$ cp /boot/config-`uname -r` ./.config
$ make menuconfig

```

*Load an Alternate Configuration File* and chose *.config*. I made no changes to the config file just exited and then:
```

$ make-kpkg clean

$ fakeroot make-kpkg --initrd --append-to-version=-linux-div-drive kernel_image kernel_headers

$ cd ..

$ dpkg -i linux-image-2.6.37.2-linux-div-drive_2.6.37.2-linux-div-drive-10.00.Custom_i386.deb 

$ dpkg -i linux-headers-2.6.37.2-linux-div-drive_2.6.37.2-linux-div-drive-10.00.Custom_i386.deb

$ update-grub

$ reboot

```

When rebooting I found these messages:
> [    0.164898] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000cc000-0x000cffff] conflicts with Video ROM [mem 0x000c0000-0x000cf3ff]
[    0.164967] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000d0000-0x000d3fff] conflicts with Adapter ROM [mem 0x000cf800-0x000d0fff]

```

$ uname -a
Linux mybox 2.6.37.2-linux-div-drive #1 SMP Fri Feb 25 14:16:02 PST 2011 i686 GNU/Linux

```

I do have any problem using the system right now. But I would like to know if this will mess up my system. And how to fix this.

I'm also attaching the complete dmesg output.

Thank you.

*_edit: sorry forgot to attach the dmesg output file. file was very long so attaching output in 4- parts._*

---

### Post by Bjorn Helgaas on 2011-06-30
The host bridge window conflict messages do not cause a problem, and you can ignore them.  I plan to change them from errors to informational.

---

