---
title: "Booting XP from external drive with Grub2"
date: 2010-01-21
forum: General Help
---

### Post by michy99 on 2010-01-21
I was given an external USB drive which has Windows XP Pro on the first partition. I can mount and access the partition with no problem. When I run update-grub, it finds the XP partition and creates a menu entry for it. But when I select it from the Grub menu, I get an error that the device is not found.

Results of sudo fdisk -l```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00086c27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1736    13944388+  83  Linux
/dev/sda3            3188        4865    13478535    5  Extended
/dev/sda4            1737        3187    11655157+  83  Linux
/dev/sda5            3188        4764    12667221   83  Linux
/dev/sda6            4765        4865      811251   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 13.7 GB, 13676544000 bytes
255 heads, 63 sectors/track, 1662 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003c157

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1662    13349983+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x119b119a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6486    52098763+   7  HPFS/NTFS
/dev/sdc2            6487       14230    62203680    7  HPFS/NTFS
/dev/sdc3           14231       17533    26531347+   5  Extended
/dev/sdc5           14231       17533    26531316   83  Linux
```The XP is on sdc1.

The relevant section of grub.cfg:```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 48289188289175a2
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```Any help would be appreciated.

---

### Post by oldfred on 2010-01-21
Unless your device.map is unusual, I would think it sees it as the third drive.

set root=(hd2,1)
drivemap -s (hd0) ${root}

Windows needs to think it is the first drive, so the drivemap command swaps it to the first drive, but it still shows hd0. I would check /boot/grub/device.map to make sure all three drives are shown.

I would copy your windows entry into 40_custom and change hd0 to hd2. 
gedit /boot/grub/grub.cfg
gksudo gedit /etc/grub.d/40_custom
sudo update-grub 

If it does work you can turn off os-prober until you modify system so you do not have two entries. Add this entry
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER="true"

---

### Post by michy99 on 2010-01-21
I tried that and got the same error, which is```
error: no such device 48289188289175a2
```blkid shows```
/dev/sda1: UUID="ec7a8326-4212-40ee-892c-c5b4ea0ff7e4" TYPE="ext4" 
/dev/sda4: UUID="a38bc7a8-1dbe-40aa-92fb-b6355c272845" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: LABEL="oldu" UUID="985deff3-f783-4bfc-8ebc-575ae36d13c6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="f1952220-1fec-4e08-a365-f267da5120b4" TYPE="swap" 
/dev/sdb1: LABEL="storage" UUID="435fb79f-8066-45e9-b0b7-18d2f19502a8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: LABEL="farm" UUID="98e613b7-8c95-40c8-9074-9e7606cae3f8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="48289188289175A2" LABEL="xppro" TYPE="ntfs" 
/dev/sdc2: UUID="B454052F5404F5C0" LABEL="Local" TYPE="ntfs"
```so the id seems to match. I'm going to see if the BIOS will let me boot from the external drive. (This is an old machine.)

---

### Post by oldfred on 2010-01-21
I am not sure if it was windows or something else, but I have seen where they take out the search line completely and boot.

---

### Post by michy99 on 2010-01-21
I removed the search line and got```
error: cannot get C/H/S values
```This old thing won't boot from an external drive, so I am going to swap it with my second internal drive. (It's actually an internal in an external case.) I may not get around to it until later this evening, so I'll post again when I see how it goes.

---

### Post by michy99 on 2010-01-21
Once I swapped the drives, and ran update-grub again it booted right up. So this is just a case of this ancient BIOS not being able to boot from a USB external drive. Thanks for the suggestions, anyway.

---

