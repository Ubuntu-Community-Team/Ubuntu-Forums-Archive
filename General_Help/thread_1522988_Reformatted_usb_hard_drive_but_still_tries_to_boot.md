---
title: "Reformatted usb hard drive but still tries to boot"
date: 2010-07-02
forum: General Help
---

### Post by Flexico on 2010-07-02
Like the title says, if the comp happens to reboot while the drive is plugged in, it will try to boot from it, but can't because there's no more operating system, and will just freeze. Now, I know I can switch the boot order in the BIOS, which I have, but I'd also like to remove whatever "boot-flag" remains on the drive.

I actually have two external hard drives and a thumb drive that do this. In case it matters.

---

### Post by Don1500 on 2010-07-02
> **Flexico said:**
> Like the title says, if the comp happens to reboot while the drive is plugged in, it will try to boot from it, but can't because there's no more operating system, and will just freeze. Now, I know I can switch the boot order in the BIOS, which I have, but I'd also like to remove whatever "boot-flag" remains on the drive.

I actually have two external hard drives and a thumb drive that do this. In case it matters.

OK I'm going to assume you have Ubuntu 10.04. Open GPARTED (System=>Administration=>Gparted) Have the drive plugged in and find it on in the gparted menu (upper right). There should be a column on the right side that says FLAGS. One of the partitions on the drive (this is the one you DON'T want to boot from!!!) should have the boot flag set. If this drive didn't not show a boot flag when you first opened it, you have problems I can't fix. Try to reformat the drive. OTHERWISE, make sure the drive is not mounted (there will not be any keys on the Gparted partition.) Right click on the word BOOT, uncheck the boot flag. Now click APPLY. The drive should not try to boot any more.

if you don't have gparted yet open the synaptic manager and load it. Or go here [www.gparted.net](www.gparted.net)

---

### Post by oldfred on 2010-07-03
Flags are just a setting in the partition table part of the MBR. Windows uses the flag (active partition) to know where to jump to continue booting.

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

IF you erase the partition table the drive becomes unusable. You might be able to recover with test disk as the data is still there. Change sda to whatever drive you want to write zero to. Very dangerous if you write zeros to the wrong place.
Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
dd if=/dev/sda of=/mbr.bin bs=446 count=1
Zero out MBR only of sda
dd if=/dev/zero of=/dev/sda bs=446 count=1
Zero out MBR and partition table
dd if=/dev/zero of=/dev/sda bs=512 count=1

---

### Post by Flexico on 2010-07-03
> **oldfred said:**
> Flags are just a setting in the partition table part of the MBR. Windows uses the flag (active partition) to know where to jump to continue booting.

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

IF you erase the partition table the drive becomes unusable. You might be able to recover with test disk as the data is still there. Change sda to whatever drive you want to write zero to. Very dangerous if you write zeros to the wrong place.
Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
dd if=/dev/sda of=/mbr.bin bs=446 count=1
Zero out MBR only of sda
dd if=/dev/zero of=/dev/sda bs=446 count=1
Zero out MBR and partition table
dd if=/dev/zero of=/dev/sda bs=512 count=1

Thank you very much, that worked! =D I would never have figured *that* out on my own!

---

