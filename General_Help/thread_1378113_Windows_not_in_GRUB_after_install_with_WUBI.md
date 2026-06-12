---
title: "Windows not in GRUB after install with WUBI"
date: 2010-01-11
forum: General Help
---

### Post by summersab on 2010-01-11
So, I converted a Vista user by enticing her with WUBI. She's a computer idiot, and she thinks Linux is great.

HOWEVER, she recently had Ubuntu muck up for her, so she uninstalled WUBI/Ubuntu and reinstalled it (9.10). Upon restart, GRUB presented no boot menu and went straight into Ubuntu. The funny thing is, under the GRUB configuration files, the timeout for the boot menu is set to 10. I tried the following (made sure to change the boot device to hda1,0 since fdisk shows her NTFS as /dev/sdb1):

[http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)

No luck. No boot menu, no Windows option. I also tried the following:

Manual Windows Entry (with /etc/grub.d/30_os-prober made unexecutable)
```
#! /bin/sh -e

echo "Adding Windows 43_custom" >&2
menuentry "Windows Vista 43_custom" {
insmod ntfs
set root=(hd1,0)
search --no-floppy --fs-uuid --set CFFCFF9EECFF7F49
chainloader +1
} 
```

Using THIS method, the boot loader did appear, but there was no Windows option. Odd. So, I'm at a blocking point. Yes, I was smart enough to run update-grub Thoughts? My replies may be a bit delayed - she's 2 hours away and I don't have direct access to her computer. Makes this even more fun.

---

### Post by meierfra. on 2010-01-12
Change your custom entry to

```
#! /bin/sh -e
echo "Adding Windows 43_custom" >&2
[COLOR="Red"]cat << EOF[/COLOR]
menuentry "Windows Vista 43_custom" {
insmod ntfs
set root=(hd1,0)
search --no-floppy --fs-uuid --set CFFCFF9EECFF7F49
[COLOR="Navy"]drivemap (hd0) ${root}[/COLOR]
chainloader +1
}
[COLOR="Red"]EOF[/COLOR]
```

The red code makes sure that the  menuentry is actually inserted into grub.cfg.
The blue code is sometimes necessary for booting Vista.
Make sure your custom script is executable and run "update-grub2"

You should now get a Vista entry on your grub menu. 

But since "update-grub" did not pick up your Vista, there probably is something wrong with your Vista install.
So if you are still not able to boot into Vista, follow these [instruction]("http://ubuntuforums.org/showthread.php?t=1291280") to generate and post "RESULTS.txt"

---

### Post by summersab on 2010-01-12
So, my computer illiterate friend didn't use WUBI; she installed with the Ubuntu disk and selected to use the entire drive in the partitioner. She failed to tell me that. So, I'm marking this as solved and suggest that this thread be used as a reference for those having trouble with GRUB2.

---

