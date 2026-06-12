---
title: "LUKS+LVM: No password prompt at boot"
date: 2010-11-27
forum: General Help
---

### Post by nrs on 2010-11-27
I've migrated from an Arch Linux installation, I have an existing luks+lvm encrypted setup I've reused. Unfortunately I could not use the alternate installer so I had to install from the desktop version, so that probably has something to do with it. :P 

I managed to install successfully, but the problem is described in the title. I'm not prompted for my luks password at boot and after I assume it timesout I'm dumped to the initramfs and I have to manually type:
> 
cryptsetup luksOpen /dev/blah weee
lvm vgchange -a y
exit
After which the boot process continues and I'm greeted by GDM. 

I've tried running > update-initramfs -k all -c. The result is: 
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic-pae
cryptsetup: WARNING: invalid line in /etc/crypttab - 
cryptsetup: WARNING: invalid line in /etc/crypttab - Here is my /etc/crypttab:
> 
wooger UUID=2cde028f-d9c4-4984-a1c3-18f5082 none luks
I've tried doing it by UUID and /dev/devicename.

I've also tried removing the splash option from grub to no effect.

---

### Post by nrs on 2010-11-27
bump

---

### Post by nrs on 2010-11-28
one last try. :P

---

### Post by dabeej on 2011-02-02
Remove luks at the end of the line you have.

---

### Post by riff50 on 2011-02-06
I have the same problem since a major upgrade. Is there any solution yet known?

I tried purging and re-installing all relevant components and checked the whole configuration. Everything looks ok to me.

---

### Post by Mr. Bunny on 2013-01-02
I've run into this problem as well. I moved my LVM in a LUKS partition to a new LUKS partition on RAID and edited crypttab, but I don't get prompted.

When I get dumped to the initramfs shell the RAID array is already running, so the cryptsetup luksOpen, lvm vgchange, exit works to resume booting. I haven't figured out how to change the order in which these things happen automatically.

---

### Post by oldos2er on 2013-01-02
Old thread closed.

---

