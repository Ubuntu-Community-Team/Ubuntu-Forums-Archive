---
title: "grub black screen but can still select OSs"
date: 2012-06-14
forum: General Help
---

### Post by holycow131415 on 2012-06-14
I've installed xubuntu 12.04. Before I had linux mint debian, and grub showed up with no problems. So basically my computer boots, and when grub should show to load, my monitor goes black. I can select Windows via up and down arrows when you are supposed to be seeing grub.

Commands I've run to try to fix are:

sudo grub-mkconfig
sudo update-grub
```

anthony@anthony-UD3R-SLI:~$ sudo update-grub
[sudo] password for anthony: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done


```

and I've reinstalled grub too. Grub is installed on /dev/sda. I've attached a screen shot of my partitions.

---

### Post by holycow131415 on 2012-06-16
I had to uncomment: GRUB_GFXMODE=800x600 in /etc/default/grub

Dunno why I had to do it this time, never had to before. Its like grub didnt auto set display options for my video card which is ati radeon 6700.

---

