---
title: "/boot/grub/menu.lst (Linux Mint 9 - Isadora)"
date: 2010-10-06
forum: General Help
---

### Post by projektlead on 2010-10-06
This is another great ACPI based problem:

I'm using a Toshiba Satellite L505-GS5035 with Linux Mint 9 (Isadora) 64-bit.  Upon startup I get the typical acpi/kernel errors.  So, I updated the BIOS to the newest and set the boot option "acpi=off".

This has allowed me to start a live USB of the OS.  I have installed from the live USB onto the hard drive and simply wanted to change the boot options to "acpi=off" on the hard drive.  

But I'm not getting a grub menu to choose from.  It automatically tries to startup the OS which of course fails.  I have also tried to locate the menu.lst file myself.  It should (and I could be wrong) be in /boot/grub/menu.lst, so I mounted the hd (at sda1) and navigated thru to /boot/grub/ but it isn't there.  

Anybody got a guess as to how I can fix this?

---

### Post by oldos2er on 2010-10-06
If you have no menu.lst, you're probably using grub2, so you'd want to edit /etc/default/grub, and change *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"* to *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"*

Alternately you can hold down Shift after POST, and press "e" to edit the kernel line.

---

