---
title: "Getting grub2 to recognise Fedora 13"
date: 2010-05-26
forum: General Help
---

### Post by pyedog on 2010-05-26
Hello,

I had a spare partition (hd0,3) on my hard disk that used to have some proprietary operating system installed on it that I forgot the name of.

I fancy giving Fedora 13 a go, so I installed it to the spare partition. I chose not to install a bootloader during the installation.

After loading Ubuntu back up, successfully running 'sudo grub-install /dev/sda' (Installation finished. No error reported.), and rebooting, Fedora isn't found.

Is there an easy way to get my system to boot into Fedora? Grub2 has given me nothing but problems and I wouldn't mind reverting to legacy Grub.

---

### Post by oldfred on 2010-05-26
Did you do 
sudo update-grub

That usually finds other systems. Grub legacy would only sometimes find windows and almost always required manual settings for other systems. What boot loader is Fedora using? If old grub you could have installed it to its partition and chainbooted easily. Grub2 does not like to be installed to a partition, but can be forced to.

---

### Post by pyedog on 2010-05-26
Fantastic, update-grub worked perfectly. I should have chainbooted really. I'll look into that later though, I'm gonna have a play around with Fedora for a while first.

Thanks for your help.

---

### Post by kapcom01 on 2010-05-30
i did exactly the same. I have Ubuntu lucid and i decided to check fedora. I installed fedora, ran **sudo update-grub** from within ubuntu and the option _appeared correctly on my Grub Menu_.

BUT it doesnt boot :(
I get this:
```

....
.....
VFS: Cannot open root device "..." or uknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on uknown-block(0,0)
....
.....

```

my **grub.cfg**:
```

menuentry "Fedora release 13 (Goddard) (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 90262e45-25ff-4a94-afd1-55ea2bf3967c
	linux /boot/vmlinuz-2.6.33.3-85.fc13.i686 root=/dev/sda9
}

```

i also changed the root=/dev/sda9 to root=90262e45-25ff-4a94-afd1-55ea2bf3967c but the same error eroor...

Can anyone help?

---

### Post by r_s on 2010-05-30
shouldn't it also have 
initrd /boot/initramfs-2.6.33.3-85.fc13.i686.img

---

### Post by kapcom01 on 2010-05-30
> **r_s said:**
> shouldn't it also have 
initrd /boot/initramfs-2.6.33.3-85.fc13.i686.img
Thanks you were right!:)

---

