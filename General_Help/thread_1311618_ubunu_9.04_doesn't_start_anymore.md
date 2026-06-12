---
title: "ubunu 9.04 doesn't start anymore"
date: 2009-11-02
forum: General Help
---

### Post by charly_c on 2009-11-02
hello!

i've using ubuntu since year ago and updated to ubuntu 9.04 a few months ago.

it was working fine but now it doesn't start and i get this erros:

mounting /dev /disk /by-uuid/3d9d72e5 (etc..) on/root failed: invalid argument

mounting /dev on /root/ dev failed: no susch file or directory
mounting /sys on /root/ sys failed: no susch file or directory
mounting /proc on /root/ proc failed: no susch file or directory

Target filesystem doesn't have /sbin/ init

No init found. Try passing init = bootarg

i can run the cd and access to internet. 

is there a solution? i believe i have to make some changes in the grub.lst
but i just wanted to be sure before i do anything else. can someone help me?

thanks!

---

### Post by P4man on 2009-11-02
can you read your harddrive from the livecd ?

---

### Post by Giblet5 on 2009-11-02
Try reinstalling grub:

Boot the Live CD. Open a terminal window and enter:

```
sudo fdisk -l
```

Which of the ext3 filesystems is your / filesystem?

Let's assume that it's /dev/sda1 for the rest of this, but you use the correct device from the fdisk command:

```
sudo mount /dev/sda1 /mnt -text
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo chroot /mnt bash ## DANGEROUS! ENTER COMMANDS EXACTLY!
update-grub
grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
sync;sync
reboot
```

That should fix it.

---

### Post by charly_c on 2009-11-03
hello!

thank you so much! i could fixed!!:p

it's working fine again.

---

