---
title: "ALERT! /dev/disk/by-uuid/xxxx-xxx-xxx-xx does not exist"
date: 2010-07-11
forum: General Help
---

### Post by MountainX on 2010-07-11
EDIT: this is a grub problem.

On botting up, I get this message:
ALERT! /dev/disk/by-uuid/xxxx-xxx-xxx-xx does not exist. Dropping to a shell.

at the shell, the prompt is (intramfs)

running blkid shows my / partition as expected and my swap partition.

Neither have the UUID referred to in the error message. What would be looking for a device by UUID? My /etc/fstab mounts / and swap by label.

Could this be a grub problem? If so, how would I fix it?

EDIT: the offending UUID is listed in grub.cfg. But I'm not sure how to get rid of it. This system was cloned from another running installation. That's why I'm trying not to use UUIDs.

---

### Post by dcstar on 2010-07-12
> **MountainX said:**
> EDIT: this is a grub problem.

On botting up, I get this message:
ALERT! /dev/disk/by-uuid/xxxx-xxx-xxx-xx does not exist. Dropping to a shell.

at the shell, the prompt is (intramfs)

running blkid shows my / partition as expected and my swap partition.

Neither have the UUID referred to in the error message. What would be looking for a device by UUID? My /etc/fstab mounts / and swap by label.

Could this be a grub problem? If so, how would I fix it?

EDIT: the offending UUID is listed in grub.cfg. But I'm not sure how to get rid of it. This system was cloned from another running installation. That's why I'm trying not to use UUIDs.

```
sudo update-grub
```

---

### Post by lordskid on 2010-07-12
try editing ur grub entry by pressing 'e' while the grub menu is shown

then if you know ur partition number then change the entry that says root=uuid in...
set root='(hd0,6)'
linux   /boot/vmlinuz-2.6.32-23-generic root=UUID=xxxxxxx-xxxxx-xxxxxxxxx ro 

to
set root='(hd0,6)'      
linux   /boot/vmlinuz-2.6.32-23-generic root=/dev/sda6 ro

hope this works. I had some similar problems before too. and this worked for me.

---

### Post by jondodson on 2010-07-12
I had this problem when I used a live ubuntu disc to do a "dd" clone of my system disc.  It cloned, but it wouldn't boot because of the uuid.  I tried the "root=" hack but it still wouldn't boot even though I set it to the drive, not a partition on the drive.

Anyway, long story short, I downloaded and burned a live clonezilla disc and used that instead of the ubuntu live disc.  Worked like a charm, dunno how, but it took care if all the uuid problems I was having using "dd"

---

### Post by MountainX on 2010-07-12
> **dcstar said:**
> ```
sudo update-grub
```

I wiped out everything. I'm going to start over. I'd like to understand how to do this. 

Some questions:
Q1. Can the the update-grub command to be run from the (initramfs) prompt? I don't think so...

update-grub  is a stub for running grub-mkconfig -o /boot/grub/grub.cfg to generate a grub2 config file.

Q2. How does update-grub work when booting from a Live distro when the target system will not boot? I do not see that you can specify the input config files, so the output grub.cfg intended for the target system is only based on the config of the source system (which, when booting from a Live USB, is not appropriate).

---

