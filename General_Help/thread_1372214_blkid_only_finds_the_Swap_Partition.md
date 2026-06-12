---
title: "blkid only finds the Swap Partition"
date: 2010-01-04
forum: General Help
---

### Post by NiklasFalk on 2010-01-04
This is on a Karmic 9.10 (Ubuntu Studio on a Laptop) which I restarted this morning (after about two weeks of use). Then Grub 2 (1.97 beta4) was not able to find the UUID.
blkid (after the recoveryboot fails) only finds the Swap. /dev/disk/by-uuid only contains the symlink to the swap (sda5) but no to the main ext4 partition (sda1).

blkid
/dev/sda5: UUID="d05f2f1a-c59e-4582-8eef-b1b04f1f247d" TYPE="swap"

Creating a symlink in /dev/disk/by-uuid with the "correct" UUID to ../../sda1 and then continue the boot seems to work somewhat and the filesystem works. But since I get there by using the Recover version I can't do much more and the symlink doesn't "stick" (completly unsure if it should since this is a ramdisk or similar?).
Trying to do the same with the normal boot doesn't work for me since the normal boot ends somwhere after the splash screen (infinitly waiting for the / mount to a UUID that doesn't exist.

After mount the /etc/fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=eb381fee-05f1-4c37-a249-db97030cf022 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d05f2f1a-c59e-4582-8eef-b1b04f1f247d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```Starting from a LiveUSB and using the Disk utility finds the main partition but list it as "Linux (0x83)" with no file system.
sudo fdisk -l gives
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c96a9

   Device Boot       Start         End        Blocks   Id  System
/dev/sda1   *            1        18662    149902483+  83  Linux
/dev/sda2            18663        19457      6385837+   5  Extended
/dev/sda5            18663        18457      6385837   82  Linux swap / Solaris
```sudo fdisk -lu /dev/sda1 returns
"Disk /dev/sda1 doesn't contain a valid partition table"

mount /dev/sda1 /mnt -t ext4 works and the files are all there, so the disk itself is not the cause.

I guess that manually creating the UUID symlink is just a debugging effort and there must be something that blkid is missing.
Would recreating the MBR help (just swinging in the dark here)?

Edit: Another similar thread:
[http://ubuntuforums.org/showthread.php?t=1275144](http://ubuntuforums.org/showthread.php?t=1275144)

---

### Post by Leppie on 2010-01-04
try this command and see if the uuid is listed after that:
```
$sudo /etc/init.d/udev restart
```

---

### Post by NiklasFalk on 2010-01-04
That did complain a bit about invoking init.d (something about being converted to an upstart process). If I tried as "service" it just informed me that udev was running.

But after editing the Grub2 entry (the recovery one) to point directly to root=/dev/sda1 and then booting I can now get the UUID with blkid (not the first try but the second and after that) and resuming boot works (startx etc). A new reboot with the defult Grub2 entry (using the UUID) now works as before.

Could this be a warning to get a new disk if the inability to get a UUID is hardware related?
The disk is a quite recent Sata 2.5", isn't those "SMART" enabled or similar (and there might be a tool available to analyze the amount of failures)?

---

### Post by Leppie on 2010-01-04
it could be related. maybe you can try contacting the manufacturer and see what they have to say about it?

---

### Post by NiklasFalk on 2010-01-04
Found the SMART info in the disk utility and it report no problems at all with the drive.

Hmm, lets copy/move more documents/files to the NAS (good practice anyway) and hope that the next time this happens is resolved as easilly.

I'm quess this can be called "solved" but not really (since I have no idea what action made the issue go away).

---

### Post by exXplode on 2010-03-24
Thx for your info. I had exactly the same problem. Just suddenly my second partition (my ubuntu root) was not reported any more by blkid and could not be mounted using its UUID on startup. I did a filesystem check using fsck but I think this might not be a filesystem but partition table issue...

After I booted using **linux ... root=/dev/sdaX ...** it worked again, so it is a good work-around. **blkid** did not find the partition but a **sudo tune2fs -l /dev/sda2** did actually listed the UUID. This is strange! I don't know where to report a bug...

greetings pklaus

---

### Post by _sluimers_ on 2010-04-28
I tried what was said here and edited /etc/grub.d/linux_10 where root=... to root=/dev/sda1. That didn't solve anything for me :(.

---

