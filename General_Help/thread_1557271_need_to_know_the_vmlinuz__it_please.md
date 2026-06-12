---
title: "need to know the vmlinuz *** it please"
date: 2010-08-20
forum: General Help
---

### Post by enhu on 2010-08-20
i need to know it please
kernel /boot/vmlinuz-*********-generic

please tell me the vmlinuz ****** of ubuntu 10.4LTS

i need it so i can boot myfirst drive.

i accidetally replaced grub2 with lilo  after installing slack in the 3rd drive.

---

### Post by WorMzy on 2010-08-20
If you're entering it on a command line, just press Tab twice, and it should show you all the available files with that name. Otherwise, boot a Live CD, mount the Ubuntu partition, and look in the /boot folder.

Actually, I believe that Ubuntu keeps a symbolic link to the most recent kernel in the root directory, so just try "/vmlinuz" for the kernel, and "/initrd.img" for the initrd.

---

### Post by Bachstelze on 2010-08-20
If your system is up-to-date, it's [font=monospace]vmlinuz-2.6.32-24-generic[/font].  Otherwise, decrement the 24 part until you find it.

---

