---
title: "Reinstall grub2 with LVM and /boot partition"
date: 2011-11-15
forum: General Help
---

### Post by moocan on 2011-11-15
Dear All,

I had a notebook with Ubuntu 11.10 x64 and Fedora 15 x64 with dual boot and following LVM disk configuration on /dev/sda (80 Gb):

```
/dev/sda1			/boot		100Mb
/dev/sda2 (vg_ubuntu)
/dev/vg_ubuntu/UbuVol00		/		20Gb
/dev/vg_ubuntu/UbuVol01		/home		9Gb
/dev/sda3 (vg_fedora)
/dev/vg_fedora/FedVol00		/		20Gb
/dev/vg_fedora/FedVol01		/home		9Gb
/dev/sda4			swap		10Gb
```

I decide to upgrade to Fedora 16 using LiveCD and Fedora kill my Ubuntu grub2 dual boot.

I'm trying to restore grub2 and have found many post about this and tried many solutions.
I have tried repair boot utility but "Separate /boot partition" does not appear.

I have restored a simple grub2 using Ubuntu alternate CD and can boot to ubuntu but impossible to restore grub on /dev/sda1 boot partition.
One time I only have a grub shell prompt at boot and sometimes nothing.
I have now many grub, grub2, boot, boot/grub, with many grub.cfg on /dev/sda1.

Can I format /dev/sda1 partition and reinstall grub2 for LVM dual boot ?
Must I have to reinstall all my systems ?

if someone could provide me some advices and/or steps to do it

Kind Regards

---

### Post by oldfred on 2011-11-15
I am not familiar with LVM, but know you cannot have one /boot for two different systems. You end up with overlap of some files that will cause conflicts.

Only one system is in the MBR and will boot thru the /boot partition. Ubuntu uses grub2 and Fedora just changed to grub2 with version 16, so you still have grub legacy. 

But even if both are using grub2, you can not only have one /boot. Different kernels, slight differences in versions of grub2.

---

