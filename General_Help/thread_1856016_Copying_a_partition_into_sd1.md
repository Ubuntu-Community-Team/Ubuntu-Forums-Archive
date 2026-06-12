---
title: "Copying a partition into sd1"
date: 2011-10-07
forum: General Help
---

### Post by BlueHound on 2011-10-07
Long story short, I have 3 partitions on my laptop. I want the partion sd1 replaced by the current content of sd8. I tried to delete the partition sd1, turning it into free space then copying the sd8 partion and pasting it into sd1. However, when trying to boot sd1 I got the following message.

Error: no such device < long alphanumerical number>
error: no such disk
error: you need to lead the kernal first.

I booted sd8 and took the following screen

[CENTER][IMG]http://i.imgur.com/ENriF.png[/IMG][/CENTER]

I am a bit dumbfounded over what I did wrong / what I can do to fix it and any help will be greatly appreciated.

---

### Post by oldfred on 2011-10-07
It looks like you did several installs as you have multiple LInux & swaps.

When you do major changes to a partition, it changes the UUID which is not supposed to change and both grub & fstab use the UUID to know what partition to boot and use.

You need to reinstall grub2's boot loader to use the UUIDs of sda1 and edit fstab of the install in sda1 to have its new UUID.

#list UUIDs
sudo blkid

In updating grub2, you have to correct all the UUID entires in grub.cfg. You can chroot into it or manually edit it once to boot and update with just a sudo update-grub. It will not boot until fstab is also edited.

IF your sda8 works you can add this to 40_custom to boot sda1. or from grub menu booting sda1 edit existing stanza to be this which uses device /dev/sda1 not UUIDs:

#This uses the link in / (root) to the most current kernal to boot.
menuentry "Ubuntu on sda1" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}

---

