---
title: "grub update question"
date: 2010-04-07
forum: General Help
---

### Post by lindsay7 on 2010-04-07
after doing an upgrade to 10.4 and updating grub I get this message. Can anyone tell me what this means and how do I address this

-desktop:~$ sudo update-grub
[COLOR="Red"]head: cannot open `/boot/grub/video.lst' for reading: No such file or directory[/COLOR]
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

I have never seen this grub/video.lst file

---

### Post by dcstar on 2010-04-07
> **lindsay7 said:**
> after doing an upgrade to 10.4 and updating grub I get this message. Can anyone tell me what this means and how do I address this

-desktop:~$ sudo update-grub
[COLOR="Red"]head: cannot open `/boot/grub/video.lst' for reading: No such file or directory[/COLOR]
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

I have never seen this grub/video.lst file

I have a video.lst file and it contains the following:

```
vbe
```

You may want to manually create one (with the same permissions as the other files there).

---

### Post by lindsay7 on 2010-04-07
Thanks, that got rid of the message. I wonder what that was all about.

---

