---
title: "reinstall without cd or usb support"
date: 2010-08-19
forum: General Help
---

### Post by romitkin on 2010-08-19
hello,
I installed ubuntu netbook remix on a very old laptop. in the end of installation, the cd drive just broke and not usable again.
the ubuntu is installed but extremely slow, I want to try to install something else like wattos or puppy.
the problem is - no cd drive, no boot from usb support in bios. only floppy.
I tried to go to grub and boot from the usb, but it doesn't find the usb drive...
any other ideas? (is it possible to make a bootable floppy that will allow me to boot from usb drive?)

---

### Post by snowpine on 2010-08-19
I think Puppy can be booted from a floppy (this certainly used to be the case in older versions), best to check over on their forum. :)

---

### Post by romitkin on 2010-08-19
hi, thank you for the answer, but I am thinking now that puppy is not an option, 
the problem is I have an wireless card for laptop, which doesn't have linux drivers.
I have one package that allows me to use windows drivers for linux (worked in other laptop I have) but the problem is that it is in .deb format which cannot be installed in puppy as far as I know, so I need something like wattos which is based on ubuntu and has that installer for deb files.
so is there any other way?

---

### Post by Bonster on 2010-08-19
The new Puppy Linux is now compatible with the debs in Ubuntu

---

### Post by oldfred on 2010-08-19
You should be able to use plop or grub to boot.

Plop
[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)
Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

Older use grub to boot USB
[http://64.124.13.3/hacks/USB_Boot_using_GRUB.html](http://64.124.13.3/hacks/USB_Boot_using_GRUB.html)

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)


If you have a way to create a separate 1GB partition on the hard drive you can also install from that, but you cannot install to the partition you boot from.

---

