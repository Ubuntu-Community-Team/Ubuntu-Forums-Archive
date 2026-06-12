---
title: "Windows disappeared after GRUB upgrade"
date: 2011-07-05
forum: General Help
---

### Post by joelstitch on 2011-07-05
I have my laptop with a partition for Ubuntu and one for Windows 7. I just installed Windows so the Ubuntu GRUB wasnt working. I follow the directions in [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) and I was able to install it fine but now the problem is that the GRUB loads but it doesn't give me an option to boot from Windows 7, just from Ubuntu. How can I get it to add Windows 7 to the GRUB?

---

### Post by joelstitch on 2011-07-05
Nevermind, I figured it out. I had to use this command:

```
sudo update-grub2
```

```
And I got this result:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.32-32-generic
Found initrd image: /boot/initrd.img-2.6.32-32-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
```

---

