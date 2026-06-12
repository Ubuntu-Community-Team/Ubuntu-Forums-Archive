---
title: "Can't boot after hibernating; disk by UUID does not exist"
date: 2010-08-14
forum: General Help
---

### Post by michaelg81 on 2010-08-14
I am unable to boot after hibernating my machine (Ubuntu 9.10). After selecting either the normal or the recovery mode option from GRUB, the splash screen stays up for a long time and then the boot process times out with an error:

[INDENT]Loading, please wait...
Gave up waiting for the root device. Common problems:
  — Boot args (cat /proc/cmdline)
    — Check root delay= (did the system wait long enough?)
    — Check root= (did the system wait for the right device?)
  — Missing modules (cat proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/{a bunch of numbers} does not exist. Dropping into a shell![/INDENT]

 However, my GRUB entry looks different than the one in the solution suggested here:

    [http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

Here's my GRUB entry, after having already attempted to edit it per another forum post. The first four lines are exactly as they were before I removed them (I made note of them before deleting them). These four lines reappeared after my editing attempt. So the remaining lines might not be exactly what I had on the initial failure. I seem to remember that all disk references were by uuid.#
 ```

	recordfail=1
	if [-n ${have-grubenv}]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)  #note: this may have been set to the UUID String#
	search --no floppy  --fs-uuid --set <uuidString>
	linux boot/vmlinuz-2.6.31-9-rt root=UUID=<uuidString> ro   quiet splash
	initrd /boot/initrd.img-2.6.31-9-rt
```
	
Here's my unsuccessful editing attempt:
```

	set root=(hd0,5)
	search --no floppy -fs-uuid --set /dev/<myLinuxVol>
	linux boot/vmlinuz-2.6.31-9-rt root=/dev/<myLinuxVol> ro   quiet no splash
	initrd /boot/initrd.img-2.6.31-9-rt
```

Before I really mess something up, I thought I'd ask for help. 

!!! NOOB ALERT !!!
Please be detailed and explicit, giving the exact syntax for each command, which programs (e.g., shell) to use, and how to launch those programs, if I need to be root, etc., etc.

Thanks a bunch. Ubuntu and its community really rocks. I'd never get Linux running if it hadn't been for you guys (and gals).

Michael

---

