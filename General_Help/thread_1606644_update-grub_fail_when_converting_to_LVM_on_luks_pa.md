---
title: "update-grub fail when converting to LVM on luks partition"
date: 2010-10-26
forum: General Help
---

### Post by Seq on 2010-10-26
I'm trying to migrate my LVs over to a Luks volume (prompt on password at boot). Unfortunately, as soon as I add my luks-encrypted physical volume to my volume group, I'm no longer able to update my grub configuration. I've detailed my steps below:

I've created and unlocked my encrypted partition with the following:
```
sudo cryptsetup -c aes-cbc-essiv:sha256 -y -s 256 luksFormat /dev/sdb1
sudo cryptsetup luksOpen /dev/sdb1 crypto_agilityssd
```

My /etc/crypttab looks like this:
```
# <target name>	<source device>		<key file>	<options>
# cryptswap1 /dev/dm-2 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
crypto_agilityssd /dev/sdb1 none luks
```

So far so good. The device is accessible in /dev/mapper. I've created a physical volume on the device, as shown:
```
$ sudo pvs
  PV         VG          Fmt  Attr PSize   PFree 
  /dev/dm-4              lvm2 --    46.00g 46.00g
  /dev/sda4  vg_thinkpad lvm2 a-   184.69g 31.66g
```

At this point, I can run `sudo update-grub` successfully.  However, if I add vgexpand, I can no longer run update-grub:
```
$ sudo vgextend vg_thinkpad /dev/mapper/crypto_agilityssd 
  Volume group "vg_thinkpad" successfully extended
chris@Thinkpad:~$ sudo update-grub
Generating grub.cfg ...
/usr/sbin/grub-probe: error: Couldn't find PV pv1. Check your device.map.
```

Does anybody know what the issue might be? My google-fu seems to be failing.

---

### Post by Seq on 2010-10-26
It looks like it is failing while calling the following command.
```
grub-probe --device /dev/mapper/vg_thinkpad-lv_root_maverick --target=abstraction
```

That seems to produce the same error as above.

```
$ sudo grub-probe --device /dev/mapper/vg_thinkpad-lv_root_maverick --target=abstraction
grub-probe: error: Couldn't find PV pv1. Check your device.map.
```

---

### Post by Seq on 2010-10-27
It appears that update-grub preserves pre-existing settings from /boot/grub/grub.cfg. It was persisting an 'insmod lvm' directive from my pre-luks system where I did not have a non-lvm /boot partition.

`rm /boot/grub/grub.cfg && update-grub` solved the issue.

I have marked my [bug #667060]("https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/667060") invalid.

---

