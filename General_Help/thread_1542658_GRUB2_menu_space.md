---
title: "GRUB2 menu space?"
date: 2010-07-30
forum: General Help
---

### Post by Sonybuntu on 2010-07-30
Is there a way to make a menu space so that my GRUB2 menu looks like this:

**Before**

[I]Linux Mint 9
Linux Mint 9 (Recovery Mode)
Memtest 86+
Windows 7 Ultimate
Windows Recovery Partition[/I]

**After**

[I]Linux Mint 9
Linux Mint 9 (Recovery Mode)
Memtest 86+
                   
Windows 7 Ultimate
Windows Recovery Partition[/I]

---

### Post by zylvere on 2010-07-30
Yes, it's possible.


Here's what you do:  

The /boot/grub.cfg is the actual file used by the GRUB loader, it says to not edit it, with good reason, but don't worry.

What you will do it **gedit** the /boot/grub.cfg file and then locate an entry like: 

```
menuentry "GNU/Linux, Linux 2.6.32-22-generic" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set a25a2616-3285-4b4d-92a9-eb1c752d2d51
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=a25a2616-3285-4b4d-92a9-eb1c752d2d51 ro  
	initrd	/boot/initrd.img-2.6.32-22-generic
}
```

And then change it to:

```
menuentry "  " {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set a25a2616-3285-4b4d-92a9-eb1c752d2d51
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=a25a2616-3285-4b4d-92a9-eb1c752d2d51 ro  
	initrd	/boot/initrd.img-2.6.32-22-generic
}
```

It will still be a selectable menu entry but it will give you the desired effect. Save and reboot.

Cheers.

---

### Post by oldfred on 2010-07-31
I add a spacer, also like having reboot & Halt for those occassions when I went to the wrong boot as I can boot different drives also:

menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

You do have to count the blank line if you do not use the first line with number 1 as default boot. Once I set it to the blank line as default boot and wondered why I had trouble.:)

I do this all in 40_custom for my additional entries.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

