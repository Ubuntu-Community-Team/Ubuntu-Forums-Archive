---
title: "USB Automounts Before fstab in 10.04"
date: 2011-02-28
forum: General Help
---

### Post by mpcusack on 2011-02-28
Hi.

I'm sure someone has had this problem, but I couldn't find it anywhere on the forums.

I have a computer with a ext4 formatted drive attached via usb. I had this set up previously in fstab (using its UUID) to be mounted as /home/me/data2 and everything worked great. 

After a recent upgrade to 10.04 I started getting warnings on boot about data corruption. After my initial scare, time fsck'ing from the live cd, and a lot of troubleshooting I found that the error wasn't due to a corrupt disk, but to trying to double mount the partition.

Apparently sometime in the boot process before mountall the usb drive was detected and that partition was being automounted as /media/usb0.

What's the right way to go about fixing this so that I can still mount the drive where I want it. All I can think of would be 1) letting it mount as /media/usb0 and just symlinking, but that seems like a hack. or, 2) disable automounting all together, but I would like to still have that enabled for other drives/usb sticks.

How can I stop partitions that are set to be mounted by fstab from being automounted first?

Thank everyone for your advice in advance.

---

### Post by dcstar on 2011-03-01
> **mpcusack said:**
> Hi.

I'm sure someone has had this problem, but I couldn't find it anywhere on the forums.

I have a computer with a ext4 formatted drive attached via usb. I had this set up previously in fstab (using its UUID) to be mounted as /home/me/data2 and everything worked great. 

After a recent upgrade to 10.04 I started getting warnings on boot about data corruption. After my initial scare, time fsck'ing from the live cd, and a lot of troubleshooting I found that the error wasn't due to a corrupt disk, but to trying to double mount the partition.

Apparently sometime in the boot process before mountall the usb drive was detected and that partition was being automounted as /media/usb0.

What's the right way to go about fixing this so that I can still mount the drive where I want it. All I can think of would be 1) letting it mount as /media/usb0 and just symlinking, but that seems like a hack. or, 2) disable automounting all together, but I would like to still have that enabled for other drives/usb sticks.

How can I stop partitions that are set to be mounted by fstab from being automounted first?

Thank everyone for your advice in advance.

fstab is **not** for removable devices.

If you want a removable device to be mounted consistently, give the partitions unique labels and they will be mounted in /media under the label name.

---

