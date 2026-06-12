---
title: "GRUB2 help"
date: 2010-01-06
forum: General Help
---

### Post by Hwest on 2010-01-06
Could someone please tell me how to remove OS's from the GRUB boot menu, and also, how can I change the default booter from Ubuntu to a different OS and edit timeout? Please give me a straight answer, no redirecting to other sites please.
Thanks,
Hamish

---

### Post by cariboo on 2010-01-06
Since not many of us are experts on grub2 yet, have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1195275"), by an expert.

---

### Post by ajgreeny on 2010-01-06
Removing OSs from the list is not straightforward as it was in legacy grub, but can be done.  However, it is necessary to know exactly what you want to remove and what you want to remain from the OSs on your machine.

For the time interval you need to edit the appropriate line in **/etc/default/grub**, which says **GRUB_TIMEOUT=10** by default.  Change that to the number of seconds you need.

For the default OS to boot, you can either change the line **GRUB_DEFAULT=0** to the number you want in the menu, or you can edit the file **/etc/grub.d/40_custom**  and rename it **09_custom** and make it executable. In that, add the info needed to boot the OS you want instead of ubuntu.  The new number of this custom file means it will be run before the 10_linux file, and that OS will be first in the menu.  The entry in the custom file needs to be in this pattern
```
menuentry "Linux Mint 8 Helena, linux 2.6.31-17-generic (/dev/sdb3)" {
    set root=(hd1,3)
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=1cf34e83-4b6f-40b6-b2d1-5e0d35c95f7d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
```the {} brackets are needed, so don't remove them.

In this file you can also setup similar entries for the full list of linux distros you want to appear in the menu, and then make the 10_linux file non-executable or they will all appear twice.

---

