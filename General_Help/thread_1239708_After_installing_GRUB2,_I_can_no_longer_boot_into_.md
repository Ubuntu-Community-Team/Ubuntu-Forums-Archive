---
title: "After installing GRUB2, I can no longer boot into my other partition"
date: 2009-08-13
forum: General Help
---

### Post by komputes on 2009-08-13
After installing GRUB2/Ubuntu 9.10 on a LUKS encrypted partition (using the alternate CD), I can no longer boot into my other partition.

I have a computer with one drive and multiple partitions. To simplify the drive layout it I have included the following attempt at a diagram/explanation:

```

/dev/sda1 [ /boot ]
/dev/sda2 [ Extended container START
-- /dev/sda8 [ / - Ubuntu 9.04]
-- /dev/sda9  [ blank ]
-- /dev/sda10 [ swap ]
/dev/sda2   Extended container STOP]

```As you can see, I have a separate /boot partition which holds GRUB and the various kernel images (initrd/vmlinuz). As long as I was using GRUB 0.97-29, I did not have any problems.

Now this is what I did to mess it up:

1) I booted from the Ubuntu 9.10 Alpha alternate (text-install) CD

2) Using the debian system installer, I set up /dev/sda9 to be LVM-over-encrypted_volume. This device will be mounted to /

3) Using the debian system installer, I set up /dev/sda10 to be LVM-over-encrypted_volume. This device will be used as encrypted swap

4) I selected the existing /dev/sda1 ( /boot ) to be mounted as /boot.

5) Once the devices set up, the installer started by installing GRUB. It detected that a legacy GRUB was on /dev/sda1 and asked me if I wanted to write over it with GRUB2 (1.96). A dialog with an empty line (which should have a command in it) showed up. The dialog presented the following message:

```

[!] Configuring grub-pc
The following linux command line was extracted from the kopt parameter in GRUB Legacy's menu.lst. Please verify that is is correct and modify it if necessary.

[                                                  ]
<Go Back>         <Continue>

```Afterwards, the installation went through, and I was able to reboot into my new Ubuntu 9.10 alpha installation. The problem happened when I rebooted and attempted to go into my old 9.04 installation on /dev/sda1. It seems that when GRUB2 generated grub.cfg from the legacy menu.lst, it did not copy UUID information properly into the new syntax. The GRUB legacy script assumes that because I set up a LVM, that now all devices are on the LVM managed, when I don't think that they are.

The layout after the Ubuntu 9.10 alpha installation looks like this:

```

/dev/sda1 [ /boot ]
/dev/sda2 [ Extended container START
-- /dev/sda8 [ / - Ubuntu 9.04]
-- /dev/sda9  [ crypt-luks ]
--- /dev/mapper/cryptdisk-karmic
-- /dev/sda10 [ crypt-luks ]
--- /dev/mapper/sda10_crypt
/dev/sda2   Extended container STOP]

```I cannot boot into Ubuntu 9.04 which is the problem I would like to resolve. When I select a kernel from Ubuntu 9.04, I just get a blinking underscore in the top left corner. Here is a line from the backed up legacy menu.lst followed by that same line in the new grub.cfg after being imported:

menu.lst
```

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        1768a7ec-e0ce-8fa4-814b-2e628de7c2b2
kernel        /vmlinuz-2.6.28-13-generic root=UUID=e1b20064-8204-4150-be5e-83bd537defc8 ro quiet splash vga=773 
initrd        /initrd.img-2.6.28-13-generic
quiet

```grub.cfg
```

menuentry "Ubuntu, Linux 2.6.28-13-generic" {
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1768a7ec-e0ce-8fa4-814b-2e628de7c2b2
    linux    /vmlinuz-2.6.28-13-generic root=/dev/mapper/cryptdisk-karmic ro   quiet splash
    initrd    /initrd.img-2.6.28-13-generic
}

```Any help would be appreciated. I hope that I have provide enough information to diagnose the issue.

:neutral:

---

### Post by komputes on 2009-08-14
To get it to work, I had to get the UUID's by running "sudo blkid" and then I placed them in grub.cfg like so:

```
menuentry "Ubuntu, Linux 2.6.28-13-generic" {
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set $UUID_OF_PARTITION_WITH_/BOOT
        linux   /vmlinuz-2.6.28-13-generic root=UUID=$UUID_OF_PARTITION_WITH_/   quiet splash
        initrd  /initrd.img-2.6.28-13-generic
}
```

---

### Post by komputes on 2009-09-16
Every time a new kernel gets installed, grub regenerated grub.cfg.

I need to modify the grub.cfg to the following to be able to boot into Jaunty:
==
menuentry "Ubuntu, Linux 2.6.28-13-generic" {
 set root=(hd0,1)
 search --no-floppy --fs-uuid --set 1768a7ec-e0ce-8fa4-814b-2e628de7c2b2
 linux    /vmlinuz-2.6.28-13-generic root=UUID=e1b20064-8204-4150-be5e-83bd537defc8 ro   quiet splash
 initrd    /initrd.img-2.6.28-13-generic
}
==

-OR-

==
menuentry "Ubuntu, Linux 2.6.28-13-generic" {
 set root=(hd0,1)
 search --no-floppy --fs-uuid --set 1768a7ec-e0ce-8fa4-814b-2e628de7c2b2
 linux    /vmlinuz-2.6.28-13-generic root=/dev/sda8 ro   quiet splash
 initrd    /initrd.img-2.6.28-13-generic
}
==


If anyone has a better way, please let me know.

---

