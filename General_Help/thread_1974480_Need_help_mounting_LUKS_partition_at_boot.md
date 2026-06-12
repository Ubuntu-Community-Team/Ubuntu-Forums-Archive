---
title: "Need help mounting LUKS partition at boot"
date: 2012-05-06
forum: General Help
---

### Post by vcrpcant on 2012-05-06
Hi,

I'm on 10.04 with a LUKS LVM encrypted system.

Now, I've added a second hard disk which I previously encrypted also with LUKS (sdb).
It has only one ext3 partition (sdb1) which I can mount manually.

I want this sdb1 partition to mount automatically at boot, asking the LUKS passphrase, but I'm having a hard time achieving this.
I've already googled a lot, and tried editing crypttab, fstab and updating initram; but, no success.
I suspect this might have something to do with me renaming the disk label previously and messed around with the device name.

CRYPTTAB
sda5_crypt UUID=cfe341e4-b2b1-47fe-91cd-d3861881afe3 none luks
c34dd6c9-570b-4e4f-ae84-c61de84a9946 /dev/sdb1 none,luks retry=1

FSTAB
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/ubuntu-root /               ext4    errors=remount-ro 0       1
UUID=6a95dccb-f5d6-41f6-bc46-b7eed026f936 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu-swap_1 none            swap    sw              0       0
/dev/mapper/c34dd6c9-570b-4e4f-ae84-c61de84a9946 /mnt ext3 defaults 0 2

INITRAM I've tried both seen at different webpages:
update-initramfs -u -k all
update-initramfs -k all -c

I believe there must be a simple solution.
Can anybody shed some light in here?

---

### Post by smurphy on 2012-05-06
Write a startup script that asks for the password. Make sure it is set to stop the boot-up process and is excluded from "parallelisation" of the upstart system.

---

### Post by vcrpcant on 2012-05-07
Thanks for your reply, but is that the only way?
If so, I'd prefer start all over from scratch :(

---

### Post by vcrpcant on 2012-05-10
Bump..

---

