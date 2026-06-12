---
title: "Newbie in need of help in mounting a volume"
date: 2009-08-27
forum: General Help
---

### Post by darrhel on 2009-08-27
I am completely new to Ubuntu, and I have created a persistent bootable USB pendrive copy of Jaunty Jackalope. I find it exciting to try a new OS, and I am thrilled that it is so good considering it is free.

At first I can access my Windows partitioned drives from inside Ubuntu, but now I can't. I've been getting an error message just like this:

"unable to mount the volume
according to mtab, /dev/sda2 is already mounted on /media/Vista"

What causes this? How can this be corrected? How can this be prevented?

I have been bugged by this error for two days; I googled for answers but to no avail, so I re-installed Ubuntu on my USB pendrive and now the volumes work fine. But I have configured my system already and don't want to go through that again if ever that error appears again. As far as I know the drives are okay and are accessible from within windows, and I also scanned them and shut the machine properly so I know my drives are okay.

I have googled high and low but I can't get a straight answer and solution to this.

Thank you and forgive my noobish approach about this matter.

---

### Post by doas777 on 2009-08-27
ok run these two commands and post the output:
```
sudo fdisk -l
sudo mount
```

that will list your disks/partitions, and then show all the volumes mounted.

---

### Post by P4man on 2009-08-27
edit: I should learn to read before posting

---

### Post by darrhel on 2009-08-27
> **P4man said:**
> edit: I should learn to read before posting
It's okay. :D

but just for the heck of it, I'm posting what you asked:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c435ab7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275       15839   116984832    7  HPFS/NTFS
/dev/sda3           15839       23127    58541052    7  HPFS/NTFS
/dev/sda4           23127       30402    58430464    7  HPFS/NTFS

Disk /dev/sdb: 4051 MB, 4051697664 bytes
255 heads, 63 sectors/track, 492 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         493     3956672    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(491, 254, 63) logical=(492, 150, 42)

Disk /dev/sdc: 2062 MB, 2062548992 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009f056

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         251     2014176+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(249, 254, 63) logical=(250, 193, 7)
ubuntu@ubuntu:~$ sudo mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sdb1 on /cdrom type vfat (rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/fuse on /home/ubuntu/.gvfs type fuse (rw,nosuid,nodev,user=ubuntu)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda2 on /mnt type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/MAO type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda2 on /media/ACER type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /media/Downloads type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
ubuntu@ubuntu:~$

---

### Post by doas777 on 2009-08-27
well it does look like your drives are all mounted to /media/* so they shoudl all be accessible, but the output of your mount command is a real mess. I;ve never seen one with many duplicate entires before. no idea what is causing it, but that is likely the cause of your error (as it was already mounted, as the message said.)

are you shutting down your OS or hibernating/suspending it when you are done with a session?

---

### Post by darrhel on 2009-08-27
Yes, I was wondering about that rather long output myself.

Anyway, I am properly shutting down my OSes, Windows and Ubuntu alike.

UPDATE: I have just shut down Ubuntu and rebooted it, and lo and behold, the volumes are *AGAIN* not available. One thing that I observed is when Ubuntu is shutting down, a long set of messages appeared and all that I remembered reading is "end_request: I/O error" (or something like that) repeated many times over with a bunch of numbers. Whatever causes these error? I'm stumped.

---

### Post by doas777 on 2009-08-27
I guess my recomendation would be to configure the mount in /etc/fstab rather than using the userspace driver (fuseblk).

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by P4man on 2009-08-27
remember: he has this problem on a live cd (well, usb stick) ! he shouldn't need to mess with fstab. Im not sure that fully explains the messy mount output though.

The "end_request: I/O error" however.. is usually just that. An I/O error. Could indicate a problem with the disk or stick (although ive seen that error on perfectly good disks as well, so dont panic just yet.

Still, if you get the cd somewhere, try booting that, and see if that lets you mount those windows drives?

---

### Post by scouser73 on 2009-08-27
Here is a tutorial on mounting an external hard drive: [[COLOR="Red"]**Mount External Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/").

---

### Post by darrhel on 2009-08-27
i probably found a temporary solution.

this is what I did:

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# sudo umount /media/DATA
umount: /dev/sda3: not mounted
umount: /media/DATA: not found
umount: /dev/sda3: not mounted
umount: /media/DATA: not found
root@ubuntu:/home/ubuntu#

then I went to Places, right clicked my volume, clicked 'Mount' and it worked!

But I bet this will happen again once I shut down and log back on. So I need some explanation and a long-term solution for this.

By the way, thanks to those who posted here regarding this matter.

---

### Post by P4man on 2009-08-27
It looks like you tried mounting 3 or 4 volumes as /media/DATA.
Can you post the output of 

```
cat /etc/fstab
```

?

---

### Post by darrhel on 2009-08-27
> **P4man said:**
> It looks like you tried mounting 3 or 4 volumes as /media/DATA.
Can you post the output of 

```
cat /etc/fstab
```

?

ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$

---

### Post by darrhel on 2009-08-28
bump bump

so... anyone?

after precarious tinkering, I typed the command: 

root@ubuntu:/home/ubuntu# sudo umount -a

and mounted the drives from the GUI and it worked.

Is this it? Is it safe?

---

