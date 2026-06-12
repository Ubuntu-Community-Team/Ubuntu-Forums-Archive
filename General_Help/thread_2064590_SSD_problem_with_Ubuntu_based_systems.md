---
title: "SSD problem with Ubuntu based systems"
date: 2012-09-29
forum: General Help
---

### Post by Imre Mehesz on 2012-09-29
Hello,

I recently got a SSD hard drive (CorsAir) - Originally it had Windows7 operating system on it, but I decided to wipe it all together.

First I installed Mint Linux on it. The very first time with EXT4 it was extremely slow, the second time with EXT2 it was very very fast (as it should be :), however, after an update and reboot, the system was unable to boot again (no errors, nothing, just blank screen)

Then, I installed Lubuntu 12.04 on it (thinking that would be better). Same result, EXT4 very slow EXT2 good. until this morning, all of a sudden I wasn't able to boot again (so far I installed Linux on this 4 times already :/ I don't wanna go back to Windows!!!)

If I boot with a LIVE CD, i'm getting the following results:
GParted GUI, says: 
[FONT="Courier New"]Partition Table: MSDOS (why??)
Partition: /dev/sda1 ext2 80GB ... boot (flag)
/dev/sda2 extended 
  /dev/sda5 swap[/FONT]

Now my fdisk says the following: 
[FONT="Courier New"]sudo fdisk -l /dev/sda1 

Disk /dev/sda1: 86.0 GB, 86003154944 bytes
255 heads, 63 sectors/track, 10455 cylinders, total 167974912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

**Disk /dev/sda1 doesn't contain a valid partition table**[/FONT]

... and ...

[FONT="Courier New"]sudo fdisk -l

Disk /dev/sda: 90.0 GB, 90028302336 bytes
255 heads, 63 sectors/track, 10945 cylinders, total 175836528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006e2c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   167976959    83987456   83  Linux
/dev/sda2       167979006   175835135     3928065    5  Extended
/dev/sda5       167979008   175835135     3928064   82  Linux swap / Solaris
lubuntu@lubuntu:~$[/FONT] 

what am I doing wrong? how can I fix this?

thank you,
--iM

---

### Post by stepking2 on 2012-09-29
Have you tried upgrading the firmware of the SSD? Corsair has had some stability problems, especially Force 3 series.

---

### Post by Imre Mehesz on 2012-09-29
**Stepking2** thanks, they said it on their website that the firmware should be the latest one on production (although, I don't know if it's a FORCE 3 device or not!) - and it actually running fine as long as I don't reboot after the first reboot :P

a little more info that I gathered since last time:

[FONT="Courier New"]lubuntu@lubuntu:~$ hal-find-by-property --key block.device --string /dev/sda |xargs -i lshal -u "{}"
udi = '/org/freedesktop/Hal/devices/storage_serial_Corsair_CSSD_F80GBP2_10296506580010170216'
  block.device = '/dev/sda'  (string)
  block.is_volume = false  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_Corsair_CSSD_F80GBP2_10296506580010170216'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_3f6_scsi_host_scsi_device_lun0'  (string)
  info.product = 'Corsair CSSD-F80'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_Corsair_CSSD_F80GBP2_10296506580010170216'  (string)
  info.vendor = 'ATA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/host0/target0:0:0/0:0:0:0/block/sda'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.drive_type = 'disk'  (string)
  storage.firmware_version = '1.1'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = false  (bool)
  storage.model = 'Corsair CSSD-F80'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = 'mbr'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 90028302336  (0x14f61ae000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = 'Corsair_CSSD-F80GBP2_10296506580010170216'  (string)
  storage.size = 90028302336  (0x14f61ae000)  (uint64)
  storage.vendor = 'ATA'  (string)[/FONT]

... and ...

[FONT="Courier New"]lubuntu@lubuntu:~$ hal-find-by-property --key block.device --string /dev/sda1 |xargs -i lshal -u "{}"
udi = '/org/freedesktop/Hal/devices/volume_uuid_64467d4b_ad96_4c26_b4ac_de6f835d948f'
  block.device = '/dev/sda1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 1  (0x1)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_Corsair_CSSD_F80GBP2_10296506580010170216'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_Corsair_CSSD_F80GBP2_10296506580010170216'  (string)
  info.product = 'Volume (ext2)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_64467d4b_ad96_4c26_b4ac_de6f835d948f'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/host0/target0:0:0/0:0:0:0/block/sda/sda1'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ext2'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '1.0'  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec', 'acl', 'user_xattr'} (string list)
  volume.mount_point = ''  (string)
  volume.num_blocks = 167974912  (0xa031800)  (uint64)
  volume.partition.media_size = 90028302336  (0x14f61ae000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.start = 1048576  (0x100000)  (uint64)
  volume.size = 86003154944  (0x1406300000)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '64467d4b-ad96-4c26-b4ac-de6f835d948f'  (string)[/FONT]

btw, I really have no idea what these are, I'm just gathering all this stuff by googling things :/

thanks,
--iM

---

### Post by xb12x on 2012-09-29
I think the partition table on /dev/sda should show up as "msdos". From what I remember that's just referring  to the format of the partition table and not what file systems it points to. I just checked my partition table (from Ubuntu) and it's "msdos".

Now the reason /dev/sda1 shows up as 
"Disk /dev/sda1 doesn't contain a valid partition table"
is because /dev/sda1 is the file system, not the partition table (so to speak).

What you're seeing is sda vs sda1.

So I don't see the problem there. 

By the way, my Ubuntu 12.04 installation is running from an SSD. The installation was straight forward, however I did a manual partitioning and a re-format during the installation to completely remove the previous O.S.  I've never had to change any disk-related parameters. 

When  you do find the answer please post it.

---

### Post by Imre Mehesz on 2012-09-29
okay, so I re-installed everything again (x2).

It seems like the **EXT4** type is completely "useless" for me, it is very very slow, install takes about an hour and starting up Chrome takes 5 mins. 

So, I re-re-installed it again with **EXT2** (install is about 20 minutes, launching chrome is instant) - logged in and rebooted the machine about 3 times, everything worked fine. 

Then I hard-reset it (like a power failure), first time it was OK, second time (and from that on) never came back, but I could see the hard drive blinking from time to time, so I hit **Ctrl+Alt+F1** and got console access, indicating that "the system on / is not ready yet". 

It also gave me some options (try to fix (**F**), that failed, and try to fix manually (**M**), with that I was able to run `**sudo cfdisk**` where everything seemed normal, but just in case I ran the WRITE command again, rebooted and viola, the system came back to life ...

I assume this is not the normal behavior of an SSD drive, it might be something else within my machine, I'm not sure, but very weird non the less ...

thanks everybody for the help!

--iM

---

### Post by BicyclerBoy on 2012-09-29
AFAIK
Your sda1 partition should have mount-point as "/"
 volume.mount_point = '/'  (string)

You could fix from boot CD & using GParted etc
Probably need to reinstall grub to that disk MBR after..
.
A good linux disk setup idea is to have another separate partition mounted (mount point) as /home
(& another type swap)

Linux has a virtual filesystem structure  with all devices mounted into it.
The filesystem does not exist just in a partition.

EXT4 is a journalled filesystem format..it should be fast on a SSD ...
I have no problems with intel SSD using ext4 format (2 yrs old from 10.10 ?)

---

### Post by pqwoerituytrueiwoq on 2012-09-29
have you enabled AHCI (as opposed to IDE) in your bios?
have you configured [FONT=Courier New]/etc/fstab[/FONT] (noatime and discard) to make your ssd happy?
i am using a corsair nova ssd i am also using a 500gb hdd for personal files 
i have this in my [FONT=Courier New]/etc/rc.local[/FONT] file
```
SSD=`/sbin/blkid -U "a7bc74de-0ab3-48f8-a159-693f8bccb3cb" | sed 's/\/dev\///;s/[1-9]//g'`
echo deadline > /sys/block/$SSD/queue/scheduler
echo 1 > /sys/block/$SSD/queue/iosched/fifo_batch
```this is my [FONT=Courier New]/etc/fstab[/FONT] file
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                           <mount point>  <type>  <options>                         <dump>  <pass>
proc                                      /proc           proc   nodev,noexec,nosuid               0       0
# / was on /dev/sda1 during installation
UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb /               ext4   **discard,noatime**,errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=5153a0b4-bfe4-4a91-82c9-f6cbfd5b2018 /home           ext4   defaults                          0       2
# /mnt/HardDisks was on /dev/sdb5 during installation
UUID=51b2b46b-891c-490c-b8a6-a878595194b6 /mnt/HardDisks  ext4   defaults                          0       2
# /mnt/DiskImages was on /dev/sdb6 during installation
UUID=89068a31-dc74-4dad-bf5f-8bfec96850de /mnt/DiskImages ext4   defaults                          0       2
# /var was on /dev/sdb2 during installation
UUID=5cae72de-be5c-4586-90ec-c65ce056555b /var            ext4   defaults                          0       2
# /tmp was made a ram disk after installation
**tmpfs                                     /tmp            tmpfs  defaults,noatime,mode=1777        0       0**
# swap was on /dev/sdb4 during installation  /etc/initramfs-tools/conf.d/resume
UUID=477b1811-dcf3-4bd5-8f12-fed3b5754a01 none            swap   sw                                0       0
# move /root to /home/root to reduce wear on ssd (cause i am paranoid)
**/home/root                                /root           bind   defaults,bind                     0       0**
```
never put swap on a ssd (will wear it out if you actually use swap)

---

### Post by zero2xiii on 2012-09-30
Hay,

Just a thought on the ext4 being slow. Because it is a journaled file system, you might have to boot the computer and leave it on for a while to allow all the 'first boot overhead' to finish up first.

Also as stated by previous posters, SSD's need a slightly different configuration than normal drives. Such as the BIOS settings mentioned and also some boot options in the grub config sometimes and then last but not least the fstab.

For more details on what settings and what what to change for SSD operation and optimization refer to these two links:
[http://tombuntu.com/index.php/2012/04/26/setting-up-ubuntu-on-an-ssd/](http://tombuntu.com/index.php/2012/04/26/setting-up-ubuntu-on-an-ssd/)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

Cherz and good luck :)

---

### Post by dcstar on 2012-10-01
Any SSD to be reused in this manner needs a complete **Secure Wipe** to reset all the available blocks on the device - this is clearly outlined on every SSD supplier's web site that I have looked at.

Reusing old SSDs without doing this - a "format" or new Partition Table is just not good enough - risks  having the SSD hardware believing that there are sill many blocks in use so there are no spare blocks available to be used in the quick write cycles.

The end result is a slow SSD when anything that uses a lot of writes is run - like a Journaling file system (EXT4).

Follow the instructions on the SSD's web site and things will work correctly. This is not an Ubuntu problem - it will arise with any OS installed on an already clogged SSD.

---

### Post by Ubuntu Warrior on 2012-10-30
There is no consensus on putting a swap on SSD or not. I would say there are now more people recommending putting the swap on SSD than not - for modern SSD drives that is.

---

### Post by ubufan52 on 2012-12-19
Same problem with very slow component installs on 12.04 with ext4. Problem appears to be solved using "barrier=0" mount option described here: [http://hardforum.com/showthread.php?t=1695762](http://hardforum.com/showthread.php?t=1695762)

Based on many users complaints about Crucial V4 SSD I thought that was the problem, but a write test "dd if=/dev/zero of=/tmp/test.data bs=4k count=32k" (found at [http://stackoverflow.com/questions/9406499/how-to-get-real-read-write-speed-of-disk-in-linux](http://stackoverflow.com/questions/9406499/how-to-get-real-read-write-speed-of-disk-in-linux)) showed that the SSD was performing according to spec.

---

### Post by BicyclerBoy on 2012-12-20
AFAIK Can also use keyword "nobarrier" for ext3 & ext4 filesystems on SSD.

Just a warning about formatting new large HDD etc with std distro tools.
The GParted version in 12.04 is badly out-dated..

---

