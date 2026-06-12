---
title: "mount: special device /dev/sdb2 does not exists"
date: 2012-03-13
forum: General Help
---

### Post by OtherHuman on 2012-03-13
Hello: I´m newbie to Ubuntu but not to Unix.
I´ve copied with dd a whole disk to another identical disk as a quick method for backup.
But when I try mounting new disk as root for example: mount /dev/sdb1 /mnt I get 

mount: special device /dev/sdb1 does not exists

I can see it in my /dev/ directory the device /dev/sdb , but not the /dev/sdb1,2..etc
When i check my /etc/fstab i see:

proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=dd86154f-52e2-43f8-a83e-435c46a3b4cf /      ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=60bb6df4-8746-47a6-a22f-a7098f0ffe59 none   swap    sw   0       0

so maybe udev is not aware of my disk?
Do you know what should I do to get my disk "mountable" ?
Thanks

---

### Post by Ghost_Mazal on 2012-03-13
Double check if you have the device name correct with

```
sudo fdisk -l
```

Maybe you have the device name wrong ?

---

### Post by OtherHuman on 2012-03-13
Thanks
The device seems to be there in the disk

root@:~# fdisk -l /dev/sdb 
...other things...
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         994     7977984   83  Linux
/dev/sdb2             994        1045      407553    5  Extended
/dev/sdb5             994        1045      407552   82  Linux swap / Solaris

---

### Post by OtherHuman on 2012-03-13
Ok.I rebooted and the disk and devices are there.
BUT, now system has boot from the /dev/sdb new disk !!! And I didn´t touch the GRUB config at all...
So, did a grub-setup /dev/sda, rebooted and all seems to be Ok again: i have my partitions mounted from /dev/sda and now i can mount /dev/sdb in /mnt

But I have no idea what happened...Any idea?. Specially important: how udev discovers a new disk without reboot?

---

