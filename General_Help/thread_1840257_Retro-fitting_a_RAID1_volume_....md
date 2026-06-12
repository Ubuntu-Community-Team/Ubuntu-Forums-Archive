---
title: "Retro-fitting a RAID1 volume ..."
date: 2011-09-07
forum: General Help
---

### Post by Jethro_uk on 2011-09-07
I have a 9.10 Ubuntu system, I use as a media server. I started with a 1TB drive, volume "A". I have now fitted an identical drive, and formatted it to be Volume "B".

Both are ext4 format.

I now want to somehow combine the two drives into a mirrored RAID, so that if one disk goes belly-up, I can recover (presumably just swap the faulty disk out).

Volume "A" is about 30% free - obviously I want to keep the existing data.

I was going to use the Webmin tool, but this is not listing my drives as available for RAID, so I suspect there's more to this than meets the eye. A quick google seems to suggest that you need to create a RAID *before* you put any data on the disk.

Can anyone suggest a guide to do what I want.

e2a: these disks are NOT the main OS disks. They are totally dedicated data disks. I am not concerned about RAIDing the system disk, as it's small enough to have a Clonezilla copy I can restore very quickly. So there are no complications with GRUB ...

---

### Post by Jethro_uk on 2011-09-08
OK, for those that want to know, here's what I found out ...

The trick is to create the RAID array, using the NEW disk, and telling the mdadm program that the other disk is missing. Thusly


```
mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 missing
```

This will create a new level1 (mirrored) RAID array at /dev/md0, and assign the device /dev/sda1 to it.

from that point, if you click on "Linux RAID" in Webmin, it will show the array, and you can format it.

Once formatted, you can mount it, as a disk in it's own right ... I did this to /mnt/RAID

You can then copy all the data on your original disk, to /mnt/RAID.

Once you have all the data you need on /mnt/RAID, you need to wipe the partitions on the "old" disk.

Then use Webmin to add the old disk to the RAID array. This will then start to recover the array, and start to mirror the data.

e2a: you can monitor the rebuild process with this command:

```
watch cat /proc/mdstat
```

---

### Post by Jethro_uk on 2011-09-10
just a couple of wee add ons ...

1) this will not create a persistent array. If you want it to start at boot, you need to issue this command:

```
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

This will start the RAID array. You then need to tell the system to mount that array as a drive using your favourite tool. Personally I use Webmin, which allows you to mount the array, and specify "Mount at boot" when you save the mount point.

---

