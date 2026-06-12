---
title: "What is the meaning of these symlinks in /?"
date: 2010-12-17
forum: General Help
---

### Post by SaturnusDJ on 2010-12-17
```
:/$ ls -ao

lrwxrwxrwx   1 root    33 2010-11-30 08:03 initrd.img -> boot/initrd.img-2.6.32-26-generic
lrwxrwxrwx   1 root    33 2010-09-29 13:29 initrd.img.old -> boot/initrd.img-2.6.32-25-generic

lrwxrwxrwx   1 root    30 2010-11-30 08:03 vmlinuz -> boot/vmlinuz-2.6.32-26-generic
lrwxrwxrwx   1 root    30 2010-09-29 13:29 vmlinuz.old -> boot/vmlinuz-2.6.32-25-generic

```

I don't understand the inner workings of GRUB and the boot part and will try to spend more time on it coming weeks...but, I got /boot at a own partition. Why does these symlinks (from within /) exist and redirect to /boot? Won't it make a own /boot partition useless if / is still needed or are these symlinks not used at boot?

---

### Post by QLee on 2010-12-17
[QUOTE=SaturnusDJ]```
:/$ ls -ao

lrwxrwxrwx   1 root    33 2010-11-30 08:03 initrd.img -> boot/initrd.img-2.6.32-26-generic
lrwxrwxrwx   1 root    33 2010-09-29 13:29 initrd.img.old -> boot/initrd.img-2.6.32-25-generic

lrwxrwxrwx   1 root    30 2010-11-30 08:03 vmlinuz -> boot/vmlinuz-2.6.32-26-generic
lrwxrwxrwx   1 root    30 2010-09-29 13:29 vmlinuz.old -> boot/vmlinuz-2.6.32-25-generic

```I don't understand the inner workings of GRUB and the boot part and will try to spend more time on it coming weeks...but, I got /boot at a own partition. Why does these symlinks (from within /) exist and redirect to /boot? Won't it make a own /boot partition useless if / is still needed or are these symlinks not used at boot?[/QUOTE]

These are somewhat of a leftover from the oldschool way of booting, although they can still be used to advantage today if one chooses to.

They link to your current kernel image and initrd (initial ramdisk) and the .old are your previous ones. Like GRUB keeps new and old lines after upgrade.

---

### Post by SaturnusDJ on 2010-12-17
So...IF (I am not going to do it) I remove the links...nothing will change, and booting will still go as normal?

---

### Post by QLee on 2010-12-17
You may remove them and if you're using GRUB in the default way your system will still boot.

Likely the next kernel upgrade, when the version changes,  would recreate the symlink for the new kernel though and the upgrade after that would likely rename to .old and write a new symlink. (I haven't tried that, can't be absolute sure what the package manager would do if it found none, but probably as I stated) However, they are just symlinks, don't take much room, if you really want to be sure you could try it and see.

Think carefully about what you are asking, they are links that currently GRUB is not using for anything, how could their presence or absence affect the way GRUB boots your system? If you remove them, what will change is that they will no longer be there.

---

### Post by oldfred on 2010-12-17
Some with lots of installs, turn off osprober or do not run it when the other system is updated. But still boot the newest kernel using the symlink.

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest boatable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

This way you do not have to boot into the install you use to boot to run osprober to get the updated kernel in any other install.

---

### Post by QLee on 2010-12-17
[QUOTE=oldfred]Some with lots of installs, turn off osprober or do not run it when the other system is updated. But still boot the newest kernel using the symlink.

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest boatable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

This way you do not have to boot into the install you use to boot to run osprober to get the updated kernel in any other install.[/QUOTE]

Yup, that what I was referring to in post 2. With "...although they can still be used to advantage today if one chooses to."

However it's not what the OP was asking.

---

### Post by SaturnusDJ on 2010-12-17
I indeed assumed they had no use. It would have been terrible when they had because it would mean you won't get anything if the OS partition is unavailable.

I won't remove them. I just wondered what use they have.

---

### Post by QLee on 2010-12-18
[QUOTE=SaturnusDJ]... It would have been terrible when they had because it would mean you won't get anything if the OS partition is unavailable.
...[/QUOTE]

Well, if the OS partition is unavailable you won't get anything anyway. In addition, if an unavailable partition is the partition that the MBR portion of GRUB is looking for /boot on, you won't even get the GRUB menu.

---

