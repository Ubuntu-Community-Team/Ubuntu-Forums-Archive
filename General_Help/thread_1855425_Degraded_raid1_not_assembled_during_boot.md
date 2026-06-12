---
title: "Degraded raid1 not assembled during boot"
date: 2011-10-06
forum: General Help
---

### Post by kuchera68 on 2011-10-06
I am currently testing my raid1 setup to make sure that I can recover from the loss of a hard drive. I was able to simulate a drive failure using the mdadm -f command, and everything seemed to run fine, I could remove the drive and add it back in. The array was rebuilt and no problems occurred.

Then I attempted to do a hardware failure simulation by pulling the power cable on one of the drives. However I get this message during the boot process:

" The drive for /media/raid is not ready.... S to skip or M for Manual "

I would have thought that the raid device would have been started as degraded, but the /dev/md0 device is never even created. 

Here is some data from the system after the hard drive power cable has been pulled and the error message appears at boot:

```

sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="50083D3C083D2280" TYPE="ntfs" 
/dev/sda2: LABEL="Windows 7" UUID="7C804F50804F0FD6" TYPE="ntfs" 
/dev/sda3: LABEL="MEDIA2" UUID="4EBC943DBC94220F" TYPE="ntfs" 
/dev/sda5: UUID="d2a6a15b-3f06-4f23-ade3-427515494456" TYPE="ext4" 
/dev/sda6: UUID="d5ccf484-e8c5-4b14-b825-a4e0b0daabb4" TYPE="swap" 
/dev/sdb1: UUID="3e866a53-4f26-6953-0983-b95d086ca8e1" LABEL="TV:0" TYPE="linux_raid_member" 

cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb1[1](S)
      1463183079 blocks super 1.2
       
unused devices: <none>

```Here is the relevant information when both drives are present and the array is assembled during the boot.

```

sudo blkid
/dev/sdb1: UUID="3e866a53-4f26-6953-0983-b95d086ca8e1" LABEL="TV:0" TYPE="linux_raid_member" 
/dev/sdc1: UUID="3e866a53-4f26-6953-0983-b95d086ca8e1" LABEL="TV:0" TYPE="linux_raid_member" 
/dev/sda1: LABEL="System Reserved" UUID="50083D3C083D2280" TYPE="ntfs" 
/dev/sda2: LABEL="Windows 7" UUID="7C804F50804F0FD6" TYPE="ntfs" 
/dev/sda3: LABEL="MEDIA2" UUID="4EBC943DBC94220F" TYPE="ntfs" 
/dev/sda5: UUID="d2a6a15b-3f06-4f23-ade3-427515494456" TYPE="ext4" 
/dev/sda6: UUID="d5ccf484-e8c5-4b14-b825-a4e0b0daabb4" TYPE="swap" 
/dev/md0: UUID="90f69727-40fa-4e37-888d-363b647fc6b6" TYPE="ext3"

cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[0] sdc1[1]
      1463182943 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda3 on /media/MEDIA2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/md0 on /media/raid type ext3 (rw,commit=0)

```And finally the contents of my /etc/mdadm/mdadm.conf and /etc/fstab:

```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
#DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 metadata=1.2 name=TV:0 UUID=3e866a53:4f266953:0983b95d:086ca8e1


``````
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=d2a6a15b-3f06-4f23-ade3-427515494456    /    ext4    errors=remount-ro    0    1
#Entry for /dev/md0 RAID1 Device:
UUID=90f69727-40fa-4e37-888d-363b647fc6b6      /media/raid     ext3    defaults    0    2
#Entry for /dev/sda3 :
UUID=4EBC943DBC94220F    /media/MEDIA2    ntfs    defaults,nls=utf8,umask=0000,nosuid,nodev    0    0
#Entry for /dev/sda1 :
#UUID=50083D3C083D2280    /media/System_Reserved    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda2 :
#UUID=7C804F50804F0FD6    /media/Windows_7    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda6 :
UUID=d5ccf484-e8c5-4b14-b825-a4e0b0daabb4    none    swap    sw    0    0


```Does anyone see any problems with my setup? Or is this the desired results of starting with a drive missing from the raid array? When I plug the drive back in, it boots up without any messages and the drive is instantly accessible.

Thanks!

---

### Post by kuchera68 on 2011-10-06
For anyone following along, I believe I found the answer in a response to this thread [http://ubuntuforums.org/showthread.php?t=998389](http://ubuntuforums.org/showthread.php?t=998389). When asked if a degraded array should automatically start during boot someone replied with the simple statement

> Yes, arrays will not activate automatically in a degraded state.With that being the case, I believe I just need to issue the command to scan and assemble the raid device after boot. I will attempt and report my findings.

```
sudo mdadm --assemble --scan
```

---

### Post by kuchera68 on 2011-10-06
Ok, still no success in trying to mount the raid device. I have the feeling there might be something wrong with the superblocks, but I have too little knowledge to know that for sure. After booting with only one drive plugged in and selected Skip for mounting the raid device, I checked the mdstat:

cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb1[1](S)
      1463183079 blocks super 1.2
       
unused devices: <none>

```Ok, so it says the md0 device is inactive, but at least it knows that sdb1 belongs to the device. So  attempted to mount the raid device with the command

sudo mdadm --assemble --verbose --scan 
```
mdadm: looking for devices for /dev/md0
mdadm: no RAID superblock on /dev/sdb2
mdadm: /dev/sdb2 has wrong uuid.
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has wrong uuid.
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sda6: Device or resource busy
mdadm: /dev/sda6 has wrong uuid.
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: /dev/sda5 has wrong uuid.
mdadm: no RAID superblock on /dev/sda4
mdadm: /dev/sda4 has wrong uuid.
mdadm: cannot open device /dev/sda3: Device or resource busy
mdadm: /dev/sda3 has wrong uuid.
mdadm: no RAID superblock on /dev/sda2
mdadm: /dev/sda2 has wrong uuid.
mdadm: no RAID superblock on /dev/sda1
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.

```It gives a device or resource busy for sdb1, and afterwards it reports that it has the wrong uuid. I have no idea why either of these would happen, sdb1 does not appear in the mount list, how can it be busy? After that I wanted to check the /dev/sdb1 partition to see what mdadm has to say about it.

sudo mdadm -E /dev/sdb1
```
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 3e866a53:4f266953:0983b95d:086ca8e1
           Name : TV:0  (local to host TV)
  Creation Time : Thu Sep 15 20:56:31 2011
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 2926366159 (1395.40 GiB 1498.30 GB)
     Array Size : 2926365886 (1395.40 GiB 1498.30 GB)
  Used Dev Size : 2926365886 (1395.40 GiB 1498.30 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 5eb9b8fd:72b02c22:9c707762:11c27d40

    Update Time : Thu Oct  6 19:06:37 2011
       Checksum : 7b91ab7c - correct
         Events : 52


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)

```Apparently the partition /dev/sdb1 is in use. Is this because it is still part of /dev/md0? If it is part of /dev/md0, why does it report the raid device as clean with two active devices? Is this information not up to date? Where can I find out if another array is using this device?

---

### Post by kuchera68 on 2011-10-06
I finally found a workaround and a possible cause to my problem after screwing around long enough. I came upon a bug report for "raid1 boot degraded mode fails" here [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/728435](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/728435). It seemed quite similar to issue, and one of the recommended workarounds was to stop the raid device and try to reassemble.

It is all starting to make a little sense, obviously the /dev/md0 device was created and set inactive. That's why I couldn't use the assemble command. The one remaining drive was already assigned to the /dev/md0. So I issued the following commands...

```
sudo mdadm -S /dev/md0
sudo mdadm --assemble --verbose --scan
sudo mount -a
```It then successfully assembled the /dev/md0 device with only one drive, and with it mounted I could access the files. The only problem is, I had to re-add the second drive when it was reconnected. This leads to a resync. Not exactly the best option, but I'll take it.

The next step is to determine if the bugfix is already installed.

---

