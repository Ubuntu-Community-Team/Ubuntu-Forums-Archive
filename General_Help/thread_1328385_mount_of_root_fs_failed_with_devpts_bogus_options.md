---
title: "mount of root fs failed with devpts bogus options"
date: 2009-11-16
forum: General Help
---

### Post by smaring on 2009-11-16
9.10 kernel 2.6.31-15-generic x86_64

Following what seemed like minor configuration changes in an attempt to get USB working (group perms) for my VirtualBox 3.0.10 WinXP VM, I am left with a system that is unable to boot.

A regular boot yields ...

```
Mount of root filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
root@server:~#
```

a fsck of the identified / filesystem declares the fs clean.

booting in "recovery mode" shows ...

```
mountall: mount /dev/pts [552] terminated with status 32
mountall: Filesystem count not be mounted: /dev/pts
[  35.518037] devpts: called with bogus options
mount: wrong fs type, bad option, bad superblock on none,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
```

my /etc/fstab does not even have a line in it for /dev/pts

how is the mount of /dev/pts even happening?

---

### Post by Giblet5 on 2009-11-16
It sounds like your /etc/fstab is pointing to /dev/pts instead of to the / filesystem's disk drive/partition.

Can you post your /etc/fstab?

Do you know what drive/partition / is? Try plugging that into fstab instead of a UUID.

---

### Post by smaring on 2009-11-16
I just noticed that in fdisk I have a small HPFS/NTFS partition that fdisk states "Partition 2 does not end on cylinder boundry".  I don't even remember why that partition is there.  I have /boot on /dev/sda1, swap on /dev/sda3, and / on /dev/sda4

I tried the direct route within my /etc/fstab for / but it didn't help.  It currently looks similar to this:

```
/dev/sda4 / ext3 default 1 1
UUID=####### /boot ext3 relatime 0 2
UUID=####### none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
none /proc/bus/usb usbfs devgid=127,devmode=664 0 0
```

I should also mention that I keep getting console message like the following about every 30 seconds:

```

[ ##.###] usb 5-2: new low speed USB device using uhci_hcd and address 4
[ ##.###] usb 5-2: configuration #1 chosen from 1 choice

```

I'm not sure if that is relavent

---

### Post by Giblet5 on 2009-11-16
> **smaring said:**
> I just noticed that in fdisk I have a small HPFS/NTFS partition that fdisk states "Partition 2 does not end on cylinder boundry".  I don't even remember why that partition is there.  I have /boot on /dev/sda1, swap on /dev/sda3, and / on /dev/sda4

I tried the direct route within my /etc/fstab for / but it didn't help.  It currently looks similar to this:

```
/dev/sda4 / ext3 default 1 1
UUID=####### /boot ext3 relatime 0 2
UUID=####### none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
none /proc/bus/usb usbfs devgid=127,devmode=664 0 0
```

I should also mention that I keep getting console message like the following about every 30 seconds:

```

[ ##.###] usb 5-2: new low speed USB device using uhci_hcd and address 4
[ ##.###] usb 5-2: configuration #1 chosen from 1 choice

```

I'm not sure if that is relavent


That first entry should be ```
/dev/sda4 / ext3 [B]noatime,errors=remount-ro 0 1
[/B]UUID=####### /boot ext3 relatime 0 2
UUID=####### none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
none /proc/bus/usb usbfs devgid=127,devmode=664 0 0
```

Are you absolutely sure that it's ext3?

I would make the change to the / fs entry, then rebuild the grub menu and write it to disk.

Example, assumes /dev/sda4 is mounted on /mnt:
```
sudo bash ## DANGEROUS! ENTER COMMANDS EXACTLY!
mount /dev/sda1 /mnt/boot
mount -o bind /dev /mnt/dev
mount -o bind /proc /mnt/proc
chroot /mnt bash
update-grub
grub-install /dev/sda
exit
exit
```

I would expect it to work perfectly after these steps.

Don't dash my expectations... ;)

---

### Post by smaring on 2009-11-16
I booted from a live CD and ...

# mount /dev/sda4 /mnt
# mount /dev/sda1 /mnt/boot
# mount -o bind /dev /mnt/dev
# mount -o bind /proc /mnt/proc
# chroot /mnt bash
# update-grub
# grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.

same problem after reboot

# fdisk -l /dev/sda
...
/dev/sda1 ... 83 Linux
/dev/sda2 ... 7 HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3 ... 82 Linux swap
/dev/sda4 ... 83 Linux

Partition table entries are not in disk order

# grub-install --recheck /dev/sda
Probing devices to guess BIOS drives.  This may take a long time.
Could not find device for /boot: Not found or not a block device.

---

### Post by Giblet5 on 2009-11-16
Weird. It sounds like you don't have a /boot/grub/device.map file. Can you check, please?

Can you verify that, within device.map, hd0 maps to /dev/sda?

Did you change the BIOS-configured boot drive in the recent past?

---

### Post by smaring on 2009-11-16
# more /boot/device.map
(fd0) /dev/fdo
(hd0) /dev/sda
(hd1) /dev/sdb

I'm not sure if /boot/grub/stage1 is supposed to be human readable or not, but the contents looks like garbage and I can sorta make out "GRUB Geo Hard Disk Read Error"

---

### Post by Giblet5 on 2009-11-16
/boot/grub/stage1 is binary machine code.

It will, of course, contain every error that grub can generate, since that's the code that generates them.

Your device.map looks correct. Can you post your /boot/grub/grub.cfg script that was generated by update-grub? Maybe there's a clue in there.

---

### Post by smaring on 2009-11-16
I don't have a /boot/grub/grub.cfg file generated when I execute an update-grub.

I cleaned up my menu.lst and made certain the root was directly referenced instead of via UUID, but it didn't seem to help

I find it very strange that it gets all the way to the AppArmour stage of booting before it decides that it does not want to mount root.  I would think it would be already mounted if it got that far.

---

