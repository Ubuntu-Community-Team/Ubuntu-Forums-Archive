---
title: "Booting RAID1 drops to busybox"
date: 2009-11-27
forum: General Help
---

### Post by jones.79 on 2009-11-27
Hello!

After updating to a new kernel my 8.10 drops me to the busybox with

ALERT! \dev\md0 not found

I tried a lot of things i found here in the forum, but was out of luck...

Assembling the RAID1 right after dropping to the busybox via

```
mdam --assemble /dev/md0 /dev/sda1 /dev/sdb1
```works like a charm, but executing

```
/sbin/mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1
```automatically via a chmod+x´d script from

```
/etc/initramfs-tools/scripts/local-top
```and after that updating the initramfs via

```
sudo update-initramfs -u -k all


```results in 

```
cannot open device /dev/sda1: No such file or directory
/dev/sda1 has no superblock - assembly aborted

```before it drops to the busybox.

```
rootdelay=200
``` did not change a thing.

Can someone help me?

jones

---

### Post by jones.79 on 2009-11-27
Hi!

Ok, some further informations [IMG]http://www.ubuntu-forum.de/wcf/images/smilies/smile.png[/IMG]

I guess there is some sort of chaos with the UUIDs.
Here are the different results from different commands:

```

blkid /dev/md0 
/dev/md0: UUID="dce1a3b2-805d-11de-bcd6-00241d22a649" TYPE="ext3" 

``````

 blkid /dev/sda1
/dev/sda1: UUID="332625b1-e5f6-66a1-a4ca-c82164ef67d9" TYPE="mdraid" 

``````

blkid /dev/sdb1
/dev/sdb1: UUID="332625b1-e5f6-66a1-a4ca-c82164ef67d9" TYPE="mdraid" 

``````

 cat /etc/mdadm/mdadm.conf
DEVICE /dev/sda1 /dev/sdb1
CREATE owner=root group=disk mode=0660 auto=yes
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=dce1a3b2-805d-11de-bcd6-00241d22a649

``````
/boot/grub/menu.lst:
title        BOOTPARTITON - RAID Ubuntu 8.10, kernel 2.6.27-15-generic
uuid        3f3cb26a-ff37-4b8b-954c-6c43d4230e00
##root        (hd0,1)
#kernel        /vmlinuz-2.6.27-15-generic root=UUID=dce1a3b2-805d-11de-bcd6-00241d22a649 ro quiet splash locale=de_DE 
kernel        /vmlinuz-2.6.27-15-generic root=/dev/md0 ro quiet splash locale=de_DE
initrd        /initrd.img-2.6.27-15-generic

``````

sudo mdadm --detail --scan
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=b1252633:a166f6e5:21c8caa4:d967ef64

```I guess the last one is not an UUID?!?
Can someone help me to sort this out?

---

### Post by jones.79 on 2009-11-28
Solved. Problem was wrong UUID in mdadm.conf

This was the wrong mdadm.conf:

```
cat /etc/mdadm/mdadm.conf
DEVICE /dev/sda1 /dev/sdb1
CREATE owner=root group=disk mode=0660 auto=yes
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=dce1a3b2-805d-11de-bcd6-00241d22a649
```UUID has "normal" format.

After manual assembly of the RAID within the BusyBox:

```
sudo mdadm --detail --scan
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=b1252633:a166f6e5:21c8caa4:d967ef64
```You can see that there is a different kind of UUID...dont know why.

```
blkid /dev/md0 
/dev/md0: UUID="dce1a3b2-805d-11de-bcd6-00241d22a649" TYPE="ext3"
```is showing the WRONG UUID, named within the mdadm.conf

Solution: change the UUID

```
sudo mdadm --detail --scan
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=b1252633:a166f6e5:21c8caa4:d967ef64
``` This makes the mdadm.conf look like

```
...
DEVICE /dev/sda1 /dev/sdb1
ARRAY /dev/md0 level=raid1 devices=/dev/sda1,/dev/sdb1 num-devices=2 metadata=00.90 UUID=b1252633:a166f6e5:21c8caa4:d967ef64
...
```After this update the initramfs to start with the new settings.

```
sudo update-initramfs -u -k all
```That´s all. Thanks for nothing :)

---

### Post by SuaSwe on 2009-11-28
Good fix, man! :D

---

