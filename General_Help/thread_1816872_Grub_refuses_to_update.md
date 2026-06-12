---
title: "Grub refuses to update"
date: 2011-08-02
forum: General Help
---

### Post by turtle153 on 2011-08-02
After installing 11.04 grub has been playing up for me and refuses to update the grub.cfg file, which means that when I install a new kernel it keeps with booting an old version.

This means I have to open my grub.cfg file and edit it by hand everytime I get kernel updates which is a pain to do.

This is the result of update-grub:
```
thomas@Vulpecula:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda3
Found Ubuntu 11.04 (11.04) on /dev/sda5
Found Ubuntu 11.04 (11.04) on /dev/sda7
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 204
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
thomas@Vulpecula:~$
```

Here's line 204. I'm not sure where it got kernel revision 28 from, seeing as it finds rev 22 in the code above, which is the the image in /boot/
```
linux /boot/vmlinuz-2.6.35-28-generic root=UUID=5291488b-61c8-4494-95a4-9290ce8f573f ro splash vga=788 quiet splash nomodeset video=uvesafb:mode_option=>>1152x864-24<<,mtrr=3,scroll=ywrap
```

Edit: /etc/defaults/grub and files in /etc/grub.d/ haven't been edited by me

---

