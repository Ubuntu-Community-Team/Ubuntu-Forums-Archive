---
title: "make more space for ubuntu"
date: 2006-04-17
forum: General Help
---

### Post by akay56 on 2006-04-17
Hi 

I installed Ubuntu Hoary on my IBM laptop about 7-8 months back. It was a clean dual-boot intall, the other OS being WinXP. The machine has a 18 gb hard disk and the partitions I made are as follows:

/dev/hda1        ntfs        10gb         winxp partition mounted to /mnt/winxp
/dev/hda2        ext3        5.5gb       the main linux partition mounted to /
/dev/hda3        extended partition        2.5gb

on the extended partition

/dev/hda5        linux swap        1gb
/dev/hda6        fat32                 1.5gb



Now i have upgraded to Breezy and my linux partition is almost out of space. I don't use Winxp much at all now :) . i was thinking if it would be possible to take 4 or 5 gb (there is free space, only about 3gb used) from the winxp partition and add it to my linux partition.

I would like to learn how can i achieve the above with minimum damage.

Thank you all in advance.

Ash.

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=akay56]Hi 

I installed Ubuntu Hoary on my IBM laptop about 7-8 months back. It was a clean dual-boot intall, the other OS being WinXP. The machine has a 18 gb hard disk and the partitions I made are as follows:

/dev/hda1        ntfs        10gb         winxp partition mounted to /mnt/winxp
/dev/hda2        ext3        5.5gb       the main linux partition mounted to /
/dev/hda3        extended partition        2.5gb

on the extended partition

/dev/hda5        linux swap        1gb
/dev/hda6        fat32                 1.5gb



Now i have upgraded to Breezy and my linux partition is almost out of space. I don't use Winxp much at all now :) . i was thinking if it would be possible to take 4 or 5 gb (there is free space, only about 3gb used) from the winxp partition and add it to my linux partition.

I would like to learn how can i achieve the above with minimum damage.

Thank you all in advance.

Ash.[/QUOTE]

You could use a live cd such as gparted, knoppix, or even the ubuntu install cd. Take your pick :)

---

### Post by aysiu on 2006-04-17
Back up all your data in the NTFS partition and defragment it from Windows.

Go to Applications > Accessories > Terminal and type ```
sudo umount /dev/hda1
sudo apt-get update
sudo apt-get install gparted ntfsprogs
sudo gparted
``` Use GParted to resize your NTFS partition. Create a new Ext3 partition out of that space. Unfortunately, you won't be able to add more space to your Ubuntu installation, but you can put some data on this new partition. Make note of what this new partition is. For the sake of this example, let's assume it's /dev/hda7 ```
sudo cp /etc/fstab /etc/fstab_backup
sudo mkdir /data
sudo gedit /etc/fstab
``` Add in this line ```
/dev/hda7 /data ext3 defaults 0 0
``` Save ```
sudo chown -R akay:akay /data
sudo chmod -R 775 /data
```

---

