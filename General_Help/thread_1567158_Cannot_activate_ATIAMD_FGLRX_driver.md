---
title: "Cannot activate ATI/AMD FGLRX driver"
date: 2010-09-03
forum: General Help
---

### Post by RCXtest on 2010-09-03
I turned off my machine and when I turned it back on it would only boot in low res mode.

I cannot 'activate' the driver, gives me an error.

Tried following options in 10 different threads here, nothing helps.

10.04, was working fine for a month or more since upgrading.

ATI 5770 card, driver is latest.

Anyone know how to fix this?

Thanks.

---

### Post by ajgreeny on 2010-09-03
There have been some kernel upgrades recently and you may simply need to reinstall the driver, if you have not already done so.

---

### Post by RCXtest on 2010-09-03
Thanks, but nothing helps.

I cannot reinstall, uninstall, install, or activate the driver.

Everything gives an error.

---

### Post by Mark Phelps on 2010-09-03
Have no way of knowing the the solution liked below is one of the 10 different threads you tried ... but if not, and it works, at least you'll get a working display back (see Section 2):

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by RCXtest on 2010-09-04
Ya thanks I saw that one too.

I have a display working, but low res and it does not scroll, it 'skips' down line by line.

I do not even know what question to ask anymore.

Nothing I have done will allow me to uninstall catalyst driver and software.

Nor can I reinstall, tried to 'activate', tried downloading from ATI and  running the install, tried downloading FGLRX packages from Synaptic.

I do not know what updates screwed up the driver, because I rarely restart computer, it is on continuously.

What about the jockey log file after trying to activate driver? Would that tell me anything?

---

### Post by RCXtest on 2010-09-09
> **ajgreeny said:**
> There have been some kernel upgrades recently 


That turned out to be the root of my problem.

I dual boot with Win7, so I have a custom Grub2 menu.

My 40_custom file loads a specific kernel. Here is my file:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu 10.04, Linux Kernel 2.6.32-24" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 373f628c-b9e3-4c57-88bc-523e1a36667a
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=373f628c-b9e3-4c57-88bc-523e1a36667a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry "Windows 7" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 5b45624f18be92f1
    chainloader +1
}
menuentry "Ubuntu Command Line" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 373f628c-b9e3-4c57-88bc-523e1a36667a
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=373f628c-b9e3-4c57-88bc-523e1a36667a ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
```If you look at the 3rd entry, "Ubuntu Command Line", you can see that it still points to the old kernel. I have edited the 1st entry to load the new kernel.

But until I discovered this, I was booting the old kernel, and I guess it was then using parts (modules, packages?) of the new kernel.

After some adventures with Grub (hint: you cannot just delete 40_custom and then update-grub, unless you enjoy booting into the GRUB> prompt!) I updated the grub.cfg file to load the new kernel.

Then I followed instructions on this page:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

1)Problem: Need to purge -fglrx

2)Problem:  Need to fully remove -fglrx and reinstall -ati from scratch

I was then able to "Activate" the driver, reboot, and get display working normally again.

Hope this info saves someone else a full week of frustration.

---

