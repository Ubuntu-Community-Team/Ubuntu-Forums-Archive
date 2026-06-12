---
title: "how to install from an .iso on hard drive"
date: 2011-03-07
forum: General Help
---

### Post by luke0927 on 2011-03-07
I have dowloaded a new flavor I want to try on a laptop, I do not have a DVD burner and its 1.3GB...will it install on the hard disk if I can extract the ISO and just run the install from a directory, or something to that extent...basically can you install from an ISO without booting it?

Thanks

---

### Post by jerome1232 on 2011-03-07
If the laptop is capable of booting from USB and you have a usb drive at least 2 GB's, you can use unetbootin to create a bootable usb drive from which you can install Ubuntu.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by wojox on 2011-03-07
Depending on the Distro. You need the vmlinuz and the initrd. They then rename them and move them to your /boot directory and reconfigure grub to allow you to boot them.

---

