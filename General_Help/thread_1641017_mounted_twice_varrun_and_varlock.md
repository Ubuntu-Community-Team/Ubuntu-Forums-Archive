---
title: "mounted twice: /var/run and /var/lock"
date: 2010-12-08
forum: General Help
---

### Post by Skaperen on 2010-12-08
The temporary filesystems /var/run and /var/lock are always being mounted twice on my desktop running Ubuntu 10.10 amd64.  On my netbook, this does not happen with Ubuntu 10.10 i386, nor did it happen on Ubuntu 9.10 amd64 on my previous desktop.

Any idea why, or what could be mounting these twice?  One thing I see odd is the 2nd mounting is in the midst of some filesystems listed in /etc/fstab.

/proc/mounts:```
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=6154672k,nr_inodes=1538668,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/disk/by-uuid/d2ce8eef-bd9e-433d-96a1-f91c1b5aa552 / ext4 rw,relatime,errors=remount-ro,barrier=1,data=ordered 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
[B]none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0[/B]
/dev/sda2 /boot ext2 rw,relatime,errors=continue 0 0
/dev/sda4 /tmp ext4 rw,relatime,barrier=1,data=ordered 0 0
/dev/sda5 /var ext4 rw,relatime,barrier=1,data=ordered 0 0
[B]none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0[/B]
/dev/sda6 /var/log ext4 rw,relatime,barrier=1,data=ordered 0 0
/dev/sda9 /home ext4 rw,relatime,barrier=1,data=ordered 0 0
/dev/sda7 /usr ext4 rw,relatime,barrier=1,data=ordered 0 0
nfsd /proc/fs/nfsd nfsd rw,relatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/phil/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=600,group_id=600 0 0
```/etc/fstab:```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=d2ce8eef-bd9e-433d-96a1-f91c1b5aa552 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=fc64dcfb-cefa-49eb-bb70-3950d7a4f372 /boot           ext2    defaults        0       2
# /tmp was on /dev/sda4 during installation
UUID=3015c537-8b88-439e-89fb-9ce3ca89cc5b /tmp            ext4    defaults        0       2
# /var was on /dev/sda5 during installation
UUID=f29436d6-b07f-498b-8405-d20835ba1852 /var            ext4    defaults        0       2
# /var/log was on /dev/sda6 during installation
UUID=1b3aa033-f9e1-4cbb-8ba2-7ad1527c4333 /var/log        ext4    defaults        0       2
# /usr was on /dev/sda7 during installation
UUID=8b59620d-26e5-495b-b5df-350167b68275 /usr            ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=60dee8c0-c0c2-4a7e-bca7-4abc53a9b44a none            swap    sw              0       0
# /home was on /dev/sda9 during installation
UUID=4feab89e-1fba-4a07-bf80-ecaff2793ad0 /home           ext4    defaults        0       2
```/etc/mtab:```
/dev/sda3 / ext4 rw,errors=remount-ro,commit=0 0 0
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
/dev/sda2 /boot ext2 rw 0 0
/dev/sda4 /tmp ext4 rw,commit=0 0 0
/dev/sda5 /var ext4 rw,commit=0 0 0
/dev/sda6 /var/log ext4 rw,commit=0 0 0
/dev/sda9 /home ext4 rw,commit=0 0 0
/dev/sda7 /usr ext4 rw,commit=0 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/phil/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=phil 0 0
```

---

### Post by bj615 on 2010-12-10
i'm not an expert on this, but.. maybe your /lib/init/fstab could shed some light on this?

---

### Post by Laslodamus on 2013-02-07
I have been chasing this problem for about a year or so. Still no progress on it. I believe most of the people don't even know it is happening. If on boot up you look at your screen (nosplash)it will become almost instantly visible what is happening.
The dead give away is your temperature gauge(lmsensors). If it shows approx 60 to 70 degrees in Celsius and nothing running, you can be sure that, system has been mounted twice because the temperature without anything running should be only half of that. Unfortunately I don't have the solutions. However, I believe it has something to do with the GRUB boot loader because before I have installed it this problem did not exists. Just to test my theory I have installed Ubuntu 10.10 on an other disk, same thing happened. Than I've tried to update to Version 12.10 which was successful but it did not even touch the boot loader and updated the existing files. The temperature sky rocketed to 93 degrees and the fan was blowing so hard I thought the laptop going to start flying.
Same thing... you could see on the start up screen that once it mounted itself, it waited, and mounted itself again a few second later and the inodes doubled. No matter what this should not be happening. I have spent about 20 years in the UNIX-LINUX environment and I can tell you this, I have never seen anything like this and I have never put this much effort and research into finding the solutions for it without any success. If you know the answer, please tap us into it.

---

