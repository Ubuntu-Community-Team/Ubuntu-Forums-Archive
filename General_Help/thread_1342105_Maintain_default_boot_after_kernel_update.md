---
title: "Maintain default boot after kernel update"
date: 2009-11-30
forum: General Help
---

### Post by B.Hat on 2009-11-30
So, I was all set (I had thought) with Grub2 configured for my 6th option (Windows XP) to boot as default for most of my family to use, UNTIL the kernel got updated, at which point the computer began booting to "memory test" by default, making it all-but inaccessible to the simple users in my family.

Is there a way to specify the default OS that will be OS specific, and not entry number specific?

If not, is there a way to have Ubuntu delete the old kernel version upon update so it is also removed from GRUB 2? (Yeah, I know this option isn't very safe, but it is unacceptable to have GRUB switch the default OS every time the kernel is updated.)

Thanks for your help.

---

### Post by fluffman86 on 2009-11-30
Grub has an option to only show your most recent X number of kernels, plus the recovery modes for each.  So have it show your most recent 2 or 3 kernels, which ever you prefer, and then figure out which number belongs to Windows, and after that it won't change anymore.

---

### Post by slakkie on 2009-11-30
Cat your grub.cfg (or less it):

less /boot/grub/grub.cfg

Then you will see menuentries:

```

menuentry "Ubuntu lucid (development branch), kernel 2.6.28-11-generic (on /dev/sda2)" {
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set ec8ce521-7f42-481b-981c-36357abf559c
        linux /boot/vmlinuz-2.6.28-11-generic root=UUID=ec8ce521-7f42-481b-981c-36357abf559c ro quiet splash
        initrd /boot/initrd.img-2.6.28-11-generic
}

```

Grab the entry you want to boot first.
Then create the following file 

/etc/default/grub.d/07_my_first_entry
```

#!/bin/sh
exec tail -n +4 $0
# Don't delete the tail line!

# my custom settings
menuentry "Ubuntu lucid (development branch), kernel 2.6.28-11-generic (on /dev/sda2)" {
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set ec8ce521-7f42-481b-981c-36357abf559c
        linux /boot/vmlinuz-2.6.28-11-generic root=UUID=ec8ce521-7f42-481b-981c-36357abf559c ro quiet splash
        initrd /boot/initrd.img-2.6.28-11-generic
}

```

Now run sudo update-grub (or grub-update, one of the two) and your default OS is at the top of your grub selection, no matter how many new kernels you install. Be sure to change the GRUB_DEFAULT in /etc/default/grub.

---

### Post by suresnjain on 2009-11-30
Download start up manager via synaptic/software centre  and your worries are over.o.k

---

