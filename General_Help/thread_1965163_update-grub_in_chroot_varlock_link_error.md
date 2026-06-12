---
title: "update-grub in chroot /var/lock link error"
date: 2012-04-25
forum: General Help
---

### Post by masuch on 2012-04-25
Hi,
I have got error in chroot (precise ubuntu 64bit as host as chrooted):

sudo update-grub
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.3.1-030301-i7-avx
Found initrd image: /boot/initrd.img-3.3.1-030301-i7-avx
Found linux image: /boot/vmlinuz-3.3.1-030301-i7
Found initrd image: /boot/initrd.img-3.3.1-030301-i7
Found linux image: /boot/vmlinuz-3.3.1-030301-generic
Found initrd image: /boot/initrd.img-3.3.1-030301-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found linux image: /boot/vmlinuz-3.0.0-20-generic
Found initrd image: /boot/initrd.img-3.0.0-20-generic
Found linux image: /boot/vmlinuz-3.0.0-19-generic
Found initrd image: /boot/initrd.img-3.0.0-19-generic
Found linux image: /boot/vmlinuz-3.0.0-18-generic
Found initrd image: /boot/initrd.img-3.0.0-18-generic
Found memtest86+ image: /boot/memtest86+.bin
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
  /var/lock/lvm: mkdir failed: No such file or directory
  File-based locking initialisation failed.
Found Ubuntu 12.04 LTS (12.04) on /dev/sdb6
Found Windows 7 (loader) on /dev/sdc1
Found Windows Recovery Environment (loader) on /dev/sdf1
done

Can anybody please explain me how should be properly bind /var/lock/lvm and /var/lock/dmraid in chroot (because it is going through symbolic link ... ) ?

Thank you,
Kind Regards,
M.

---

### Post by thomas_d_j on 2012-08-19
I just encountered the same problem.

Solution is to also bind /run before you chroot, like you did for /dev, /dev/pts and /proc:

```
sudo mount --bind /run  /where_you_mounted_your_chroot/run
```

---

### Post by masuch on 2012-08-30
> **thomas_d_j said:**
> I just encountered the same problem.

Solution is to also bind /run before you chroot, like you did for /dev, /dev/pts and /proc:

```
sudo mount --bind /run  /where_you_mounted_your_chroot/run
```

thanks a lot for help.

---

