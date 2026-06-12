---
title: "Trying to get an older harddrive to be useful"
date: 2010-03-09
forum: General Help
---

### Post by Freddie1984 on 2010-03-09
I have just added an extra hard drive to my computer i am running ubuntu 8.04 and the hard drive which i just added came from a computer which was running xp how would i be able to get the hard drive to mount for storage purposes only. All i would like to do is completely wipe it out. Thank you for your help in advance

---

### Post by patchwork on 2010-03-09
Do you want it to auto mount or mount on-demand?

---

### Post by Freddie1984 on 2010-03-09
I would like it to auto mount

---

### Post by patchwork on 2010-03-09
Make the mount point 
```
sudo mkdir /media/Storage #or any other suitable name
```
find the location of your drive
```
sudo fdisk -l
```
Edit your /etc/fstab
```
gksu gedit /etc/fstab
```
Add the location of your drive to your fstab.  An example-

            
/dev/sdb7          /media/Storage_Or_other_name       ext3        defaults 0 2

Obviously, if you want to format the drive as ext4, you would enter that instead of ext3


Mount the drive```
mount /dev/drive_designation /media/Storage #or other suitable name
```
Then run the gparted utility and format the drive to the desired format.

---

### Post by Freddie1984 on 2010-03-09
i did what you said and it all seemed to be going on the right track but the issue is that it still has all the original guts of the xp which it was used for prior sorry for the hassle but this will be the first time i have tried this on my linux box this is what it is displaying after i try to find the location

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6b2c6b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf584f584

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdc: 4043 MB, 4043309056 bytes
125 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      100405      247697   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(100404, 79, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(247696, 24, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       21767      271577   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(21766, 48, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(271576, 60, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      241276      491086   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(241275, 3, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(491085, 14, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?      372346      372354       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(372345, 119, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(372353, 14, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 2000 MB, 2000748032 bytes
64 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         969     1953439+   6  FAT16

---

### Post by dcstar on 2010-03-09
> **Freddie1984 said:**
> i did what you said and it all seemed to be going on the right track but the issue is that it still has all the original guts of the xp which it was used for prior sorry for the hassle but this will be the first time i have tried this on my linux box this is what it is displaying after i try to find the location
........

Use the Partition Manager to write a new partition table to the drive.

Use the Partition Manager to create and format a partition on the drive.

Install the **pysdm** package and use that to mount the new partition to somewhere on your system so you can use it (I would suggest /Storage as a mount point).

---

### Post by Barriehie on 2010-03-09
> **Freddie1984 said:**
> i did what you said and it all seemed to be going on the right track but the issue is that it still has all the original guts of the xp which it was used for prior sorry for the hassle but this will be the first time i have tried this on my linux box this is what it is displaying after i try to find the location

...muted...
/dev/sdb1   *           1        4865    39078081    7  HPFS/NTFS
...muted...


Looks like it's **/dev/sdb1** Is 40 Gbytes right for the size?

---

### Post by patchwork on 2010-03-09
It looks like you're booting linux from sda1, windows from sdb1, is that novell on sdc?  and a 2gb windows drive on sdd1.

[B]I'm guessing the 2gb windows is the drive you want to use as storage?

[/B] 

```
sudo mkdir /media/Storage && sudo mount /dev/sdd1 /media/Storage
```Then format the partition sdd1 to whatever you wish (ext3 is good and stable for linux, fat is good for linux and windows) using Gparted (System > Administration > Gparted )

and modify your fstab to include ```
/dev/sdd1 /media/Storage (format_type_you_chose) defaults 0 2
```

---

### Post by Freddie1984 on 2010-03-09
when i noticed what you guys were looking at i noticed it was picking up my flash drives this is the information minus the flashdrive

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6b2c6b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf584f584

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4865    39078081    7  HPFS/NTFS


and yes the hard drive is 40 gb so the address for the hard drive that i am trying to mount would be ?????

thanks for all the patience

---

### Post by patchwork on 2010-03-09
/dev/sdb1

---

### Post by Barriehie on 2010-03-09
After you create the mount point and edit /etc/fstab, have to be root as indicated prior, and have formatted the drive to whatever fs type you can, from the terminal:
```

mount -a
```and it will mount the drive without your having to reboot.  If you like you can also add a symbolic link to the drive on your desktop like I do, unless your nautilus preferences already do that.

---

