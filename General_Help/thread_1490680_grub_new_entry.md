---
title: "grub new entry"
date: 2010-05-22
forum: General Help
---

### Post by krishna1650 on 2010-05-22
Hello all, I have installed 10.04 recently. Already i had 8.04 on other partition, with xen kernel installed. Now, after installing 10.04, new grub is installed and only normal 8.04 entry is shown in grub entry. How can i add xen 8.04 entry in 10.04 grub. I have my previous 8.04 grub menu.lst file. Entry for xen kernel in 8.04 grub file is as follows,

title		Xen 3.2 / Ubuntu 8.04.4 LTS, kernel 2.6.24-27-xen
root		(hd0,2)
kernel		/boot/xen-3.2.gz
module		/boot/vmlinuz-2.6.24-27-xen root=UUID=b67b754e-4dda-407d-9626-400544303ecb ro console=tty0
module		/boot/initrd.img-2.6.24-27-xen
quiet

Can anyone tell how to add this entry in 10.04 grub ?
Thanks

---

### Post by johngreth on 2010-05-23
the deal with the new grub is that it auto detects all operating systems. Is there any reason why this one wouldn't get detected?
this may help: [https://wiki.ubuntu.com/Grub2#User-defined%20Entries](https://wiki.ubuntu.com/Grub2#User-defined%20Entries)

---

### Post by kansasnoob on 2010-05-23
The first thing to try is simply:

```
sudo update-grub
```

If you need more detailed help please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kansasnoob on 2010-05-23
Just some general info if you like to figure things out on your own. If "update-grub" fails to pick up that kernel you'd want to manually add it to "/etc/grub.d/40_custom" using gedit ,eg: "gksudo gedit /etc/grub.d/40_custom". The default file looks like this:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

```

Do NOT change any of those lines, but rather, below them add the new entry for that kernel. I dug up an old Info Script RESULTS.txt to compare some Hardy boot entries from it's own legacy grub and from grub 2:

```
title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=ee620c21-7f87-41fb-a7af-d868f72ce754 ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet
```

```
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set ee620c21-7f87-41fb-a7af-d868f72ce754
	linux /boot/vmlinuz-2.6.24-27-generic root=UUID=ee620c21-7f87-41fb-a7af-d868f72ce754 ro quiet splash
	initrd /boot/initrd.img-2.6.24-27-generic
}
```

You can see that the general syntax has changed greatly and the { } at the beginning and end of the boot syntax is important! Also the partition numbering has changed in grub 2.

Grub 2 still begins counting drives with 0 (zero) just as legacy grub did, but partitions now begin with 1 (one), so in your post it showed Hardy on "(hd0,2)". I'm guessing that it would now be recognized as "(hd0,3)" by grub 2.

This is a great guide:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Oh, and any time you edit any of grub 2's executable scripts you must run "sudo update-grub" for the change to appear in "grub.cfg".

---

