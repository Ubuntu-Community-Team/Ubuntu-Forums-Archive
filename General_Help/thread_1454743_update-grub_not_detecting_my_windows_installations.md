---
title: "update-grub not detecting my windows installations..."
date: 2010-04-15
forum: General Help
---

### Post by melrokz on 2010-04-15
I need to add my windows installations to the grub menu.
I have windows 7 and windows xp on hd0 and windows xp on hd1.
Using 'sudo update-grub' doesn't seem to help.
So how do i fix this?

---

### Post by melrokz on 2010-04-15
Windows 7=/dev/sda2
windows xp 1=/dev/sda3
windows xp 2=/dev/sdb1

---

### Post by melrokz on 2010-04-15
Windows 7=/dev/sda2
windows xp 1=/dev/sda3
windows xp 2=/dev/sdb1

---

### Post by darolu on 2010-04-15
I see in your mini-profile that you use 9.04 (you probably haven't updated it), remember Jaunty still uses GRUB legacy (0.97) and update-grub won't work.

If you indeed have Karmic and GRUB2, os-prober is probably not working and you'll have to add the entries manually.

Edit your 40_custom file, located at /etc/grub.d/:
```
$ gksudo gedit /etc/grub.d/40_custom
```
This is how I have my Windows partition, you'll have to change it according to your settings:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Videogames" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 400aa41b7790b28a
	drivemap -s (hd0) ${root}
	chainloader +1
}
```
The menuentry string is what you will see in your grub menu, you may want to put "windows xp/7" instead; the --fs-uuid --set number can be found with:
```
$ sudo blkid
```
Oh and remember, now in GRUB2, hd0,1 = sda1; hd1,2 = sdb2, etc...

---

### Post by melrokz on 2010-04-15
No, I do use jaunty and the legacy GRUB!
I had some issues with Karmic (downloaded via bittorrent) so I stuck to jaunty...
So, what do i do?

---

### Post by darolu on 2010-04-15
You can install "startupmanager":
```
$ sudo apt-get install startupmanager
```
If I recall correctly, this application can detect and add other OS's to your GRUB, I may be wrong though, I haven't used the app in a very long time.

Anyways, you can always fix it manually by editing the menu.list file located at /boot/grub/:
```
$ gksudo gedit /boot/grub/menu.lst
```
This is a sample of a Windows XP entry:
```
title Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1
```
In GRUB legacy, we have to use the old notation: hd0,0 = sda1, hd1,2 = sdb3, etc...

You can always reinstall grub too, boot from the LiveCD, open a terminal and run:
```
$ sudo grub

> root (hd0,0)

> setup (hd0)

> exit
```

---

### Post by oldfred on 2010-04-15
Windows combines its boot into one, the first one with the boot flag, moving boot files so grub can only boot the one that windows uses.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

If you want to boot each and the install is one a primary partition, you may be able to move boot flag and run the repairs to make each windows bootable. But then a boot from the first windows will only work for that one not all of them.

---

