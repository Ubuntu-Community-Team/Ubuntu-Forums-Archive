---
title: "New Drive Automounts to /"
date: 2010-05-02
forum: General Help
---

### Post by lonestarshack on 2010-05-02
So, I just installed lucid and the install went great. It was installed to /dev/sda on the /dev/sda1 partition. However, I'm having a heck of a time getting a new (additional) drive to do what I want it to do. So, I have a thinkpad and I insert a spare hard drive in the optical slot to the right. If I insert the drive after the OS has booted, I simply go to the Disk Utility, mount the drive, and all is well. No issues. However, if I boot up the OS while the drive is already connected, the OS boots, but the new spare drive shows up as mounted to / and is represented as /dev/sda1 which is originally where my OS was installed. I tried adding an entry in fstab for /dev/sdb1 which would represent my new ext4 partition on the spare drive, but as I thought, it actually mounts my internal drive. Any ideas?

---

### Post by sisco311 on 2010-05-02
Hi and welcome to the forums!

Please post the output of:
```
mount
cat /etc/fstab
sudo fdisk -l
sudo blkid 

```

---

### Post by lonestarshack on 2010-05-02
Here is the output without the drive installed at boot:

```

root@shackbuntu:/home/rob# mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rob)
root@shackbuntu:/home/rob# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1c8dbaf0-9705-473b-9248-18a993f6f91d none            swap    sw              0       0
root@shackbuntu:/home/rob# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00076d07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112412672   83  Linux
/dev/sda2           13995       14594     4805633    5  Extended
/dev/sda5           13995       14594     4805632   82  Linux swap / Solaris
root@shackbuntu:/home/rob# blkid
/dev/sda1: UUID="81939b9f-ad4b-4862-8945-2940548caf61" TYPE="ext4" 
/dev/sda5: UUID="1c8dbaf0-9705-473b-9248-18a993f6f91d" TYPE="swap" 

```

I'll add the output with the drive installed at boot on the next reply.

---

### Post by dino99 on 2010-05-02
is your bios checking that drive first instead your ubuntu drive ?

---

### Post by lonestarshack on 2010-05-02
Here is the output with both drives installed:

```

root@shackbuntu:/home/rob# mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rob)
root@shackbuntu:/home/rob# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1c8dbaf0-9705-473b-9248-18a993f6f91d none            swap    sw              0       0
root@shackbuntu:/home/rob# fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30402   244198583+  ee  GPT

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00076d07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13995   112412672   83  Linux
/dev/sdb2           13995       14594     4805633    5  Extended
/dev/sdb5           13995       14594     4805632   82  Linux swap / Solaris
root@shackbuntu:/home/rob# blkid
/dev/sda1: UUID="80f46ffb-2a7e-4a36-a582-16ee2ffb5dec" TYPE="ext4" 
/dev/sdb1: UUID="81939b9f-ad4b-4862-8945-2940548caf61" TYPE="ext4" 
/dev/sdb5: UUID="1c8dbaf0-9705-473b-9248-18a993f6f91d" TYPE="swap" 

```

Note: I used Disk Utility to delete/create/format the spare drive.

---

### Post by dino99 on 2010-05-02
MountManager can be set to not mount it on boot

---

### Post by lonestarshack on 2010-05-02
Thank you for letting me know about MountManager, but I simply just want the new drive to show up as /dev/sdb1 when it boots so I can simply put an entry in fstab and mount it where I need to when it boots. I know that Bios sees both of the drives, but can you clarify your first question a bit.

---

### Post by sisco311 on 2010-05-02
Sorry for the delay.


Use the UUID to mount the root partition:
```
gksu gedit /etc/fstab
```

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
**UUID=81939b9f-ad4b-4862-8945-2940548caf61**       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1c8dbaf0-9705-473b-9248-18a993f6f91d none            swap    sw              0       0
```

[thread=283131]How to fstab[/thread]
[uhelp]community/UsingUUID[/uhelp]

---

### Post by lonestarshack on 2010-05-02
Thank you sisco. I read over the two links you sent and they were very helpful. I implemented the suggestion as well as modifying the other two entries in fstab and all is well.

---

### Post by sisco311 on 2010-05-02
Cool!

Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

### Post by lonestarshack on 2010-05-02
Done. I was thinking. This is the kind of reason the average Joe won't use a linux distro for their everyday desktop. This is quite unfortunate that its not very intuitive or friendly. Regardless of this thought, I did want to thank you for your prompt response. I sincerely appreciate it.

---

