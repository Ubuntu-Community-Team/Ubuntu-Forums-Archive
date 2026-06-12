---
title: "Convert system to RAID5"
date: 2012-01-04
forum: General Help
---

### Post by mobrien118 on 2012-01-04
Hello,

I will update this post with specifics as I work through this process, and respond with comments as I have questions I have not solved.

I'll try to make this a short as possible. My end goal is to have a system using RAID5, made from my current system that has multiple partitions.

Current setup:
[LIST]
[*]2TB drive
[LIST]
[*]SWAP Partition - 2GB
[*]/ Partition - 20GB
[*]/home partition - the rest
[/LIST]
[*]750GB drive
[LIST]
[*]SWAP partition - 2GB
[*]/home/myuser/xtradata partition - the rest
[/LIST]
[/LIST]

I recently acquired 3 more of the same 2TB disk I already have. What I would like to end up with is a system with 4 identically partitioned disks, with each one like this:
[LIST]
[*]SWAP Partition - 2GB
[*]RAID1 - /boot - 1GB
[*]RAID5 - / - The rest
[/LIST]

The RAID1 partition will actually be a 4 disk RAID1 (I know that writes will be slower, but it is only for the /boot partition, and I want all disks to be "swapppable" with the same MBR so that I can pull any damaged disk and run in degraded mode, if necessary)

So, I will lay out my plan with current holes and questions. Here goes:
[LIST=1]
[*]Partition my 3 currently empty 2TB disks with the layout above
[*]Create the RAID1 and RAID5 arrays in "degraded" mode using ```
mdadm --create --verbose /dev/md1 --level=5 --chunk=32 --raid-devices=4 missing /dev/sdb3 /dev/sdc3 /dev/sdd3
``` (I used the webmin RAID interface to create the RAID1 array because I couldn't figure out how to set the "persistent superblock" option with mdadm, although I think it is simply specifying the version 0.9 superblock...)
[*]Format the drives using```
sudo mkfs.ext4 -E stride=8,stripe-width=32 /dev/md1
sudo mkfs.ext4 /dev/md0
```
[*]Copy the boot data to the new boot partition using ```
rsync -avxHAXS --delete --progress /boot /mnt/NewRAID1/
```
[*]Copy the rest of the data to the new root partition using ```
rsync -avxHAXS --delete --progress / /mnt/NewRAID5/
```
[*]Remove boot from the new root partition (rm -R /mnt/NewRAID5/boot/*)
[*]Update /etc/fstab on the new RAID5 to mount NewRAID1 as /boot and NewRAID5 as /
[*]***_???_***
[*]Remove primary disk and verify function with 3 disks in "degraded mode"
[*]Copy the "extradata" stuff over to the new array
[*]Test system functions thoroughly
[*]Partition primary disk same as other 3
[*]Add 4th disk to arrays and update fstab to use the 4th SWAP, too
[/LIST]

The ??? represents these questions:
How do I update GRUB to use these partitions appropriately?
How do I write GRUB to the disks (using the installer CD? I don't think it has mdadm on it...)?
How do I copy the MBR to each of the disks? (I guess I could just "update-grub" to each of the 4 disks, right?)

Also, if anyone has any suggestions or pointers on how I can make this better, I would love to hear them.

Thanks!

--mobrien118

---

### Post by mobrien118 on 2012-01-09
OK, so I finished this! And I made some major changes in direction, so here is the procedure. If an admin could move this to the tutorials/howtos folder, maybe that would be helpful. How does one request that?

Anyway, I discovered that you CAN boot into a RAID5 array with GRUB2, so I decided to change the partitioning scheme to this:

[LIST]
[*]RAID5 - SWAP - 2GB
[*]RAID5 - / - 10GB
[*]RAID5 - {mirror of /} - 10GB
[*]RAID5 - /home - The rest
[/LIST]

This structurally mimics the current partitioning scheme.

Here was the process:
[LIST=1]
[*]Partition my 3 currently empty 2TB disks with the layout above
[*]Create the RAID5 arrays in "degraded" mode using ```
mdadm --create --verbose /dev/mdY --level=5 --chunk=32 --raid-devices=4 missing /dev/sdbX /dev/sdcX /dev/sddX
```*Y=0,1,2 and 3 and X=1,2,3 and 4
[*]Format swap using```
mkswap /dev/md0
```
[*]Format the drives using ```
sudo mkfs.ext4 -E stride=8,stripe-width=32 /dev/mdX
```*X=1,2 and 3
[*]Mount the last raid array using ```
sudo mkdir /mnt/NewRAID1
sudo mount /dev/md3 /mnt/NewRAID1/
```
[*]Copy the /home data to the new boot partition using ```
rsync -avxHAXS --delete --progress /home/ /mnt/NewRAID1/
```
[*]Boot into ALTERNATIVE liveCD, tell it to assemble all RAID arrays (but don't set any as the shell root) and start a shell
[*]Mount original root (sdb2) and new root (md1) *It wasn't md1 at this point. I had to find it using ls -l /dev/disk/by-uuid/
[*]Copy old root to new root using ```
cp -a /media/sdb2/* /media/md1/
```
[*]Mount my home partition where it should be using ```
mount /dev/md3 /media/md1/home
```
[*]chroot into the *new* filesystem using ```
mount -o bind /proc /mount/point/proc
mount -o bind /dev /media/md1/dev
mount -o bind /dev/pts /media/md1/dev/pts
mount -o bind /sys /media/md1/sys 
cp /etc/resolv.conf /media/md1/etc/resolv.conf
chroot /media/md1
```
[*]update grub on my *NEW* disks ONLY using ```
mv /boot/grub/device.map /boot/grub/device.map.old
grub-mkdevicemap
update-grub2
grub-install /dev/sdc
grub-install /dev/sdd
grub-install /dev/sde
```
[*]Shutdown and remove old primary disk from system
[*]Boot into new system
[*]mount my old "extra data" partition
[*]copy data from my old "extra data" partition, since this wasn't copied over in the rsync of /home using ```
sudo rsync -avxHAXS --delete --progress /media/OldXtraPart/ /home/me/XtraData/
```
[*]Test system functions thoroughly
[*]Partition primary disk same as other 3 (I actually just copied the MBR using "dd if=/dev/sdb of=/dev/sda bs=512 count=1. This requires a reboot)
[*]Add 4th disk partitions to arrays (I did this using webmin, but it can be done using palimpsest or, of course, mdadm from the command line)
[*]Wait until 4th disk starts rebuilsding and *Reboot* (because grub needs the system to have been booted into with the current disk configuration, it wouldn't work before rebooting)
[*]Repeat grub-install process from above, using /dev/sda (or whatever it is now)
[/LIST]

This has my system running very nicely. Read speeds on the first partition are over 400 MB/s and at the end of the 4th partition, I'm getting about 200 MB/s, but at the beginning of this partition it is at about 330 and has a round downward slope.

Woohoo!

--mobrien118

---

