---
title: "Problem Mounting File System"
date: 2010-06-30
forum: General Help
---

### Post by jcobban on 2010-06-30
I have a 500GB SATA drive in a USB enclosure that I  use to backup my system.  My first step was to clone the 500GB drive in my computer to the USB drive.  Now I would like to use rsync to copy changes made since that cloning to the filesystem on the USB drive.  But Ubuntu will not let me mount the filesystem because it has the exact same UUID as the main filesystem!  I don't know how the UUIDs are created, but without a unique UUID I do not know how to do the mount.

---

### Post by dabl on 2010-06-30
Use "mount by-label" instead of "mount by-uuid" for the external drive.  If you have it set up in /etc/fstab, you'll have to edit the mount line to change it, after you have assigned the drive (partition) a label.

[http://www.nslu2-linux.org/wiki/HowTo/MountDisksByLabel](http://www.nslu2-linux.org/wiki/HowTo/MountDisksByLabel)

---

### Post by jcobban on 2010-06-30
> **dabl said:**
> Use "mount by-label" instead of "mount by-uuid" for the external drive.  If you have it set up in /etc/fstab, you'll have to edit the mount line to change it, after you have assigned the drive (partition) a label.

[http://www.nslu2-linux.org/wiki/HowTo/MountDisksByLabel](http://www.nslu2-linux.org/wiki/HowTo/MountDisksByLabel)

Thank you.  However this does not really address my problem.

To explain in more detail:  There are two partitions on the USB attached drive, because there were two partitions on the original drive when I cloned it.  One partition, an NTFS partition for a bootable Win7 system, spontaneously mounts and an icon appears on the desktop whenever I plug the USB drive in, even though I did nothing to fstab with respect to this partition.  I don't understand this.  Possibly it works because the corresponding NTFS partition no longer exists on the main drive because I replaced the dual boot configuration with VirtualBox so I could have both OSes running at the same time.  When I unplug the drive the icon for this Win7 partition spontaneously disappears.

I do not understand why Ubuntu is able to mount and unmount this NTFS partition spontaneously when it won't mount the EXT4 partition, without extraordinary efforts on my part.

I added an entry:

```
/dev/disk/by-label/LinuxBackup /media/linuxBackup         ext4    errors=remount-ro 0       1
```

to fstab and issue 'sudo mount -a'.  The system does seem to mount the partition.  But now I cannot **unmount** the partition.  When I unplug the USB drive the icon for the partition that I mounted by label on the desktop does **not** disappear.  When I try to explicitly unmount the drive I get an error dialog "umount: /media/linuxBackup mount disagrees with the fstab".  And when I plug the USB drive back in, the mount has to be repeated manually before I can see the contents of the partition.  If I then try to unmount the drive I get an error dialog 'umount: it seems /media/linuxBackup is mounted multiple times'!

So mount by label does **not** appear to be the solution I am looking for.

---

### Post by jcobban on 2010-07-01
I still cannot get this to work.  Automount mounts the NTFS partition but cannot mount the EXT4 partition when I plug the external drive into the USB port.  When I try to explicitly mount the partition, which appears as /dev/sdc5 in fdisk, I get an error:

```
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda5 is already mounted on /

ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2010-07-01 10:37 34E0E317E0E2DE5C -> ../../sdc1
lrwxrwxrwx 1 root root 10 2010-07-01 10:37 64E2185EE2183730 -> ../../sdc2
lrwxrwxrwx 1 root root 10 2010-07-01 10:37 f0a635ba-d2e2-491f-9984-e87d75077a6b -> ../../sdc6
lrwxrwxrwx 1 root root 10 2010-07-01 10:37 f81f4681-6cb9-46e7-9262-d5f57c723774 -> ../../sdc5
```

This confusion is obviously because f81f4681-6cb9-46e7-9262-d5f57c723774 is also the UUID of the ext4 partition on my main hard drive.

---

### Post by jcobban on 2010-07-01
I have now tried to explicitly change the UUID of the partition, but that fails:

tune2fs /dev/sdc5 -U 72fe2e64-bfe3-4019-936b-66a5f57a9061
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Permission denied while trying to open /dev/sdc5
Couldn't find valid filesystem superblock.

---

### Post by jcobban on 2010-07-01
> **jcobban said:**
> I have now tried to explicitly change the UUID of the partition, but that fails:

tune2fs /dev/sdc5 -U 72fe2e64-bfe3-4019-936b-66a5f57a9061
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Permission denied while trying to open /dev/sdc5
Couldn't find valid filesystem superblock.

Silly me.  I should have paid attention only to "Permission denied".  Of course this command needs to be run under sudo.

Now that I have unique UUIDs on all of the partitions of the USB drive, they automount.

---

