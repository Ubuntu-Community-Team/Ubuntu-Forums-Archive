---
title: "Howto Convert Read-Only Root FS to SquashFS"
date: 2010-04-05
forum: General Help
---

### Post by cmcginty on 2010-04-05
Can anyone point me in the right direction to convert my root to a squashFS image.

I currently have a working read-only root file system that I setup using the the [AUFS tutorial]("https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash").

How can I convert this to a squashFS image, and then configure initrd and grub to mount it during boot?

---

### Post by cmcginty on 2010-04-05
I'm planning on approaching like so:

1. follow squashfs steps to build the image from my root, excluding my /boot
2. dd the squashfs image onto a new partition
3. setup grub entry to pull the kernel image from /boot and mount the squashfs partition as root
4. add squashfs to initramfs-tools modules file
5. update initrd.img
6. reboot and test

Does this sound reasonable?

---

### Post by cmcginty on 2010-04-17
Bump ... I got all my hardware, so I really need to get this working now. Any pointers would be helpful.

I partitioned a second drive like so:

sdb1: /boot
sdb2: squashfs image

I installed grub on the second drive, but mounting sdb1 on top of my current /boot directory.

I rebooted, disabling sda. Got the the grub screen, but grub dies saying that the UUID does not match. I imagine update-grub script is assuming I want to boot from my root on sda1, how do you tell it to use another root?

:confused::confused::confused:

---

### Post by urs_buddy7 on 2011-04-26
HI,
Any updates on same? Were you able to meet the task?? If yes please share with community.

---

### Post by cmcginty on 2011-04-26
Here is my script I came up with. I run this inside of a VirtualBox VM where I want to convert / to a squashfs image.

```

mount --bind / /mnt
mksquashfs /mnt /root.sqsh -noappend -nopad -e /root.sqsh
dd if=/root.sqsh of=/dev/sdb2
```

At this point I create a boot partition on /dev/sdb1.

```

mke2fs -t ext2 /dev/sdb1
tune2fs -c 0 -i 0d /dev/sdb1
mount /dev/sdb1 /mnt/boot
cp -a /boot/* /mnt/boot
grub-install --recheck --root-directory=/mnt /dev/sdb
./grub.cfg.sh > /mnt/boot/grub/grub.cfg
umount /mnt/boot
umount /mnt
```

The grub.cfg.sh script outputs a config file for grub:

```

set default="0"
set timeout=1

if terminal_input console ; then true ; else
  terminal console
fi
if terminal_output console ; then true ; else
  terminal console
fi

set menu_color_normal=white/black
set menu_color_highlight=black/white

menuentry "Ubuntu, Linux" {
   set quiet=1
   insmod ext2
   set root=(hd0,1)
   linux /vmlinuz-2.6.35-28-generic root=/dev/sda2 ro  splash quiet aufs=tmpfs
   initrd   /initrd.img-2.6.35-28-generic
}

menuentry "Memory test (memtest86+)" {
   linux16  /memtest86+.bin
}

menuentry "Memory test (memtest86+, serial console 115200)" {
   linux16  /memtest86+.bin console=ttyS0,115200n8
}
```

Finally, outside of the VM, I burn the image to a CF card like so:

```

VBoxManage internalcommands converttoraw $(VBOXIMAGE) image.raw
tar cf - image.raw | gzip --fast > $(VERSION).tar.gz
sudo umount $(CFDISK)* || true
	sudo dd if=image.raw of=$(CFDISK) bs=8192
	sudo sfdisk -f $(CFDISK) < partition.info

```

The partition info is re-written with the partition.info file, because it is replaced by the dd command:

```

# partition table of /dev/sdh
unit: sectors

/dev/sdh1 : start=       63, size=    65537, Id=83
/dev/sdh2 : start=    65600, size=   982976, Id=83
/dev/sdh3 : start=  1048576, size=  6786608, Id=83
/dev/sdh4 : start=        0, size=        0, Id= 0

```

---

