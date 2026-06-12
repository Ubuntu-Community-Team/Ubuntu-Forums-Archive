---
title: "Several Mount Issues"
date: 2011-05-27
forum: General Help
---

### Post by AxelMan0 on 2011-05-27
Automount is not working on my clean install of Ubuntu 11.04. USB drives, SD cards, and CDs all fail to automount. I am able to mount the USB and SD cards manually. The CDs will not even mount manually. This is the output from
```
sudo mount -t iso9660 /dev/cdrom /media/cdrom0
``````
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```I also tried using cdrom1, scd0, scd1, sr0, sr1 as devices and they all gave the same error. I also tried a few different CDs.

here's the syslog tail

```
[21901.873056] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 10 00 00 01 00
[21901.873070] end_request: I/O error, dev sr0, sector 64
[21901.873093] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[22063.450839] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[22063.450847] sr 0:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[22063.450855] Info fld=0x10, ILI
[22063.450858] sr 0:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
[22063.450866] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 10 00 00 01 00
[22063.450880] end_request: I/O error, dev sr0, sector 64
[22063.450900] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
```I have looked over many forum posts and there are many similar threads stating "I can't mount my ipod", "I can't mount my USB stick", and the like. Here is a link to one such thread that I'm sure is about the same automount problem:

[http://ubuntuforums.org/showthread.php?t=1744890](http://ubuntuforums.org/showthread.php?t=1744890)

Yes I have automount enabled in gconf-editor. My fstab is empty except for my main hard drive, /proc, and swap. My mtab is as follows:

```
/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/johnson/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=johnson 0 0
/dev/sdb1 /media/mnt vfat rw 0 0
```The last entry is an SD card that I mounted using 'sudo mount'. As of writing this there is an audio disc in each of my 2 cd drives. Being able to mount the CDs manually would be a step forward but I really want to get automount working. I just put Ubuntu on the computer that my family uses and I want them to have a good experience with their first open source adventure.

---

