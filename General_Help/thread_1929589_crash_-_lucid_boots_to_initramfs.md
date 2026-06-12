---
title: "crash - lucid boots to initramfs"
date: 2012-02-22
forum: General Help
---

### Post by kurja on 2012-02-22
Ubuntu lucid unexpectedly hung up, even the mouse cursor wouldn\t move, I hit ctrl alt del and after like a minute the system booted and made it`s way back to the the desktop view, but I could not start any programs. I booted again, and now it goes to initramfs, saying that /dev /sys /proc can not be mounted.

I started up with the CD, and can not mount the drive (it says that the device is busy / a job is pending).

Any ideas on what to try to fix this?

---

### Post by roelforg on 2012-02-22
I assume you hd is /dev/sda here and has 1 partition.
try:
```

sudo fsck /dev/sda1

```
And post the output.

---

### Post by kurja on 2012-02-22
> **roelforg said:**
> I assume you hd is /dev/sda here and has 1 partition.
try:
```

sudo fsck /dev/sda1

```And post the output.


```
ubuntu@ubuntu:/$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```

---

### Post by roelforg on 2012-02-22
> **kurja said:**
> ```
ubuntu@ubuntu:/$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```
If you're working from a live cd,
don't mount the /dev/sda1.

Here's an updated version that should work:
```

sudo umount /dev/sda1
sudo fsck /dev/sda1

```

---

### Post by kurja on 2012-02-22
```
ubuntu@ubuntu:/$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:/$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```

:???:

---

### Post by roelforg on 2012-02-22
> **kurja said:**
> ```
ubuntu@ubuntu:/$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:/$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```:???:
Strange...
Tried rebooting the live-cd?
It'll reset the mounts.

---

### Post by kurja on 2012-02-22
> **roelforg said:**
> Strange...
Tried rebooting the live-cd?
It'll reset the mounts.
same result.

```
sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```

---

### Post by roelforg on 2012-02-22
> **kurja said:**
> same result.

```
sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```
I really  wouldn't know;
did you run the umount command before the fsck?

---

### Post by kurja on 2012-02-22
Yes, rebooted from the cd, then ran the two commands (sudo umount /dev/sda1 followed by sudo fsck /dev/sda1).

I would have expected nothing to have been mounted after rebooting from the cd, though?

---

### Post by roelforg on 2012-02-22
> **kurja said:**
> Yes, rebooted from the cd, then ran the two commands (sudo umount /dev/sda1 followed by sudo fsck /dev/sda1).

I would have expected nothing to have been mounted after rebooting from the cd, though?

Some versions of the cd automount your hd.

Try running:
```

sudo ls -la /dev/sd*
sudo ls -la /dev/hd*

```
and post the output

---

### Post by kurja on 2012-02-22
```
ubuntu@ubuntu:~$ sudo ls -la /dev/sd*
brw-rw---- 1 root disk 8,  0 2012-02-22 14:39 /dev/sda
brw-rw---- 1 root disk 8,  1 2012-02-22 14:39 /dev/sda1
brw-rw---- 1 root disk 8,  2 2012-02-22 14:39 /dev/sda2
brw-rw---- 1 root disk 8,  5 2012-02-22 14:39 /dev/sda5
brw-rw---- 1 root disk 8, 16 2012-02-22 14:39 /dev/sdb
brw-rw---- 1 root disk 8, 17 2012-02-22 14:39 /dev/sdb1
ubuntu@ubuntu:~$ sudo ls -la /dev/hd*
ls: cannot access /dev/hd*: No such file or directory
```

---

### Post by roelforg on 2012-02-22
> **kurja said:**
> ```
ubuntu@ubuntu:~$ sudo ls -la /dev/sd*
brw-rw---- 1 root disk 8,  0 2012-02-22 14:39 /dev/sda
brw-rw---- 1 root disk 8,  1 2012-02-22 14:39 /dev/sda1
brw-rw---- 1 root disk 8,  2 2012-02-22 14:39 /dev/sda2
brw-rw---- 1 root disk 8,  5 2012-02-22 14:39 /dev/sda5
brw-rw---- 1 root disk 8, 16 2012-02-22 14:39 /dev/sdb
brw-rw---- 1 root disk 8, 17 2012-02-22 14:39 /dev/sdb1
ubuntu@ubuntu:~$ sudo ls -la /dev/hd*
ls: cannot access /dev/hd*: No such file or directory
```
Wait, tell me the partition layout of your disk.
gparted will show it to you.
I suspect we're trying to fsck the wrong partition (swap?).

---

### Post by kurja on 2012-02-22
> **roelforg said:**
> Wait, tell me the partition layout of your disk.
gparted will show it to you.
I suspect we're trying to fsck the wrong partition (swap?).

It is the default partitioning, as created by ubuntu installer, on an ssd drive.

Disk utility shows the main partition as dev/sda1, an `extended partition` (whatever that is) as dev/sda2 and a swap partition as dev/sda5.

---

### Post by roelforg on 2012-02-22
> **kurja said:**
> It is the default partitioning, as created by ubuntu installer, on an ssd drive.

Disk utility shows the main partition as dev/sda1, an `extended partition` (whatever that is) as dev/sda2 and a swap partition as dev/sda5.
May i ask what sdb is?
Is it an 2e HD?

Try the fsck on /dev/sda2 i'm curious to what it'll say.

---

### Post by kurja on 2012-02-22
```
ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
```

sdb is a hdd where I store my data, the ssd is just for the operating system and applications.

---

### Post by roelforg on 2012-02-22
> **kurja said:**
> ```
ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
```sdb is a hdd where I store my data, the ssd is just for the operating system and applications.
So do i; sda = OS sdb = DATA.

Try running:
```

sudo usermod -a -G disk root
sudo umount /dev/sda1
sudo fsck /dev/sda1

```

---

### Post by kurja on 2012-02-22
still gives the same response :/

---

### Post by roelforg on 2012-02-22
> **kurja said:**
> still gives the same response :/
The annoying things with these kind of problems are that the system denies access to run checks on it.

I'm afraid i can't help you.
If your pc won't execute the commands; i'm powerless.

---

### Post by kurja on 2012-02-22
Darn. I guess I`m looking at reinstalling.

---

### Post by roelforg on 2012-02-22
> **kurja said:**
> Darn. I guess I`m looking at reinstalling.
Yep, unless someone else has any ideas.

---

### Post by HavarN on 2012-02-22
I am sorry to say this sounds like a bad harddrive failure.

Why don't you just run ```
palimpsest
``` from ALT+F2 or find Disk Utility in the menus on the LiveCD. It is pretty easy to use and it will tell you all you need to know about the state of your disks.

---

### Post by roelforg on 2012-02-22
> **HavarN said:**
> I am sorry to say this sounds like a bad harddrive failure.

Why don't you just run ```
palimpsest
``` from ALT+F2 or find Disk Utility in the menus on the LiveCD. It is pretty easy to use and it will tell you all you need to know about the state of your disks.
That i didn't think of that!!!!

---

### Post by matt_symes on 2012-02-22
Hi

Have you tried a different superblock for fsck ?

Have you tried a different version of fsck. Try fsck on Slax. That has fixed this for some people. 

What does this return ?

```
dmesg | grep sda1
```

There was a bug in fsck. See [https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/711799](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/711799) for more information

I take it it's not mounted ?

```
mount
```

Just out of interest, what does this return

```
sudo dumpe2fs /dev/sda1 | head -n20
```

Kind regards

---

### Post by kurja on 2012-02-22
> **HavarN said:**
> I am sorry to say this sounds like a bad harddrive failure.

Why don't you just run ```
palimpsest
``` from ALT+F2 or find Disk Utility in the menus on the LiveCD. It is pretty easy to use and it will tell you all you need to know about the state of your disks.

Disk utility does not show anything unusual about the disk, it appears all good. "Disk is healthy", all green in smart data.

---

### Post by kurja on 2012-02-22
> **matt_symes said:**
> Hi

Have you tried a different superblock for fsck ?

Have you tried a different version of fsck. Try fsck on Slax. That has fixed this for some people. 
Sorry, that's all greek to me.

> **matt_symes said:**
> 

What does this return ?

```
dmesg | grep sda1
```There was a bug in fsck. See [https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/711799](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/711799) for more information

I take it it's not mounted ?

```
mount
```Just out of interest, what does this return

```
sudo dumpe2fs /dev/sda1 | head -n20
```Kind regards

```
dmesg | grep sda1
[    4.353211]  sda: sda1 sda2 < sda5 >
[    6.754193] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    6.754202] EXT4-fs (sda1): write access will be enabled during recovery
[    6.758070] EXT4-fs warning (device sda1): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[    6.758078] EXT4-fs warning (device sda1): ext4_clear_journal_err: Marking fs in need of filesystem check.
[    6.758117] last sysfs file: /sys/devices/pci0000:00/0000:00:0e.1/host0/target0:0:0/0:0:0:0/block/sda/sda1/uevent
``````
mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
``````
sudo dumpe2fs /dev/sda1 | head -n20
dumpe2fs 1.41.11 (14-Mar-2010)
Filesystem volume name:   <none>
Last mounted on:          /
Filesystem UUID:          6a33afae-faa6-4c02-bbde-cc15b9a34ee1
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              3751936
Block count:              14981120
Reserved block count:     749056
Free blocks:              11382623
Free inodes:              3480754
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1020
```

---

### Post by kurja on 2012-02-22
> **roelforg said:**
> That i didn't think of that!!!!

I see you've had way too much ubuntu, I did mention using the disk utility in an earlier post :)

---

### Post by kurja on 2012-02-23
> **matt_symes said:**
> Hi

Have you tried a different superblock for fsck ?

Have you tried a different version of fsck. Try fsck on Slax. That has fixed this for some people. 



Hi,

I read up about slax, my problem drive is ext4 and if I understand correctly that is not supported by slax. Do I have other alternatives?

On a side note, I went to [http://www.slax.org/get_slax.php](http://www.slax.org/get_slax.php) to get slax but it says I can't download it unless I register for some file sharing service, special offer only 49.95 a year. Seriously?

The superblock thing I still don't understand.

---

### Post by kurja on 2012-02-23
managed to download slax anyway from that site, but I'm getting an error trying to extract it to a usb stick. hm.

```
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
```

---

### Post by kurja on 2012-02-23
downloaded puppy linux, same issue with that (iso file).

may I cuss now?

edit - tried ubuntu rescue remix, same thing happens.

---

### Post by HavarN on 2012-02-23
Could you please post the output of this command from the liveCD?```
cat /etc/mtab && cat /proc/mounts
```

If the partition still shows up in that output after you ran the umount command. Try this command before running fsck:```
sudo umount -l /dev/sda1
```

Edit:
You could also have a look at the -r switch of the umount command.

---

### Post by kurja on 2012-02-23
> **HavarN said:**
> Could you please post the output of this command from the liveCD?```
cat /etc/mtab && cat /proc/mounts
```If the partition still shows up in that output after you ran the umount command. Try this command before running fsck:```
sudo umount -l /dev/sda1
```Edit:
You could also have a look at the -r switch of the umount command.

```
cat /etc/mtab && cat /proc/mounts
aufs / aufs rw 0 0
none /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
/dev/sr0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=767104k,nr_inodes=191776,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
/dev/sr0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
tmpfs /cow tmpfs rw,noatime,mode=755 0 0
aufs / aufs rw,noatime,si=613b3d05 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=999,group_id=999 0 0
```

It does not appear as mounted, so I don't suppose umount can do anything to it. Reading up on the bug report mentioned in an earlier post in this thread, this problem is somehow caused by the boot up process trying to mount the drive but failing at it due to problems with the drive, and the failed mounting attempt somehow persists(?) so that any operations on the drive are not possible. I guess I need to find a way to boot without the system attempting to mount the drive, then it may be possible to fix the problems with fsck.

---

### Post by roelforg on 2012-02-23
> **kurja said:**
> I see you've had way too much ubuntu, I did mention using the disk utility in an earlier post :)
I guess i know so many commands that this one slipped away in a dark corner of my memory.

---

### Post by roelforg on 2012-02-23
> **kurja said:**
> 



```
dmesg | grep sda1
[    4.353211]  sda: sda1 sda2 < sda5 >
[    6.754193] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    6.754202] EXT4-fs (sda1): write access will be enabled during recovery
[    6.758070] EXT4-fs warning (device sda1): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[    6.758078] EXT4-fs warning (device sda1): ext4_clear_journal_err: Marking fs in need of filesystem check.
[    6.758117] last sysfs file: /sys/devices/pci0000:00/0000:00:0e.1/host0/target0:0:0/0:0:0:0/block/sda/sda1/uevent
```

I'm starting to believe you've got yourself a HD-failure (or at least a corrupted fs)... (Or a loose wire in your pc)

---

### Post by matt_symes on 2012-02-23
Hi

For Slax, download the iso for a CD and use that for the USB.

The Ubuntu built in usb creator may work; i have never tried it.

If not, you can try unetbootin to create the bootable USB or the dd command.

```
sudo dd if=/path/to/iso of=/dev/<device>
```

You will need to change the above command as required to point o the ISO and the correct device. It is very important to get these correct.

> Filesystem state:         clean with errors

> [    6.758070] EXT4-fs warning (device sda1): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[    6.758078] EXT4-fs warning (device sda1): ext4_clear_journal_err: Marking fs in need of filesystem check.

The problem seems to be with the journal. 

I do not think this is a hard drive failure but a filing system error.

The partition is not mounted so that is not the problem. I would try to create a bootable Slax USB and use fsck from that.

If not, you may be able to delete and recreate the journal if that is what is causing the problems. (debugfs and then tuune2fs).

I would try with Slax fsck first though as that has fixed it for other people.

EDIT:

@roelforg

> I'm starting to believe you've got yourself a HD-failure

Maybe...

Run a smart test from the command line.

```
sudo apt-get install smartmontools
```

```
sudo smartctl -t long /dev/sda
```

When it has finished (This will take a while)

```
sudo smartclt -a /dev/sda
```

Post the results back here and we can take a look.

*** Change sda above to the correct device if it is different ***

Kind regards

---

### Post by HavarN on 2012-02-23
> **kurja said:**
> It does not appear as mounted, so I don't suppose umount can do anything to it. Reading up on the bug report mentioned in an earlier post in this thread, this problem is somehow caused by the boot up process trying to mount the drive but failing at it due to problems with the drive, and the failed mounting attempt somehow persists(?) so that any operations on the drive are not possible. I guess I need to find a way to boot without the system attempting to mount the drive, then it may be possible to fix the problems with fsck.

Well... I'm not so sure about that. You can try to remount it read-only before umounting it again:```
sudo umount -r /dev/sda1
sudo fsck /dev/sda1
```

After all this is Linux, you are in full control over everything on your system. There is nothing it won't allow you to do if you have super user access.

---

### Post by kurja on 2012-02-23
> **roelforg said:**
> I'm starting to believe you've got yourself a HD-failure (or at least a corrupted fs)... (Or a loose wire in your pc)

Entirely possible.

There's this bug report [https://bugs.launchpad.net/ubuntu/+s...gs/+bug/711799](https://bugs.launchpad.net/ubuntu/+s...gs/+bug/711799) describing similar symptoms, where the problem has been solved with fsck, which apparently can't be ran when booted from the live cd (for the reasons already brought up).

---

### Post by kurja on 2012-02-23
> **HavarN said:**
> Well... I'm not so sure about that. You can try to remount it read-only before umounting it again:```
sudo umount -r /dev/sda1
sudo fsck /dev/sda1
```After all this is Linux, you are in full control over everything on your system. There is nothing it won't allow you to do if you have super user access.

I can't mount it, it just hangs for a while and then nothing.

---

### Post by kurja on 2012-02-23
> **matt_symes said:**
> Hi

For Slax, download the iso for a CD and use that for the USB.

The Ubuntu built in usb creator may work; i have never tried it.

If not, you can try unetbootin to create the bootable USB or the dd command.

```
sudo dd if=/path/to/iso of=/dev/<device>
```You will need to change the above command as required to point o the ISO and the correct device. It is very important to get these correct.


I'll give that another try, I tried earlier and couldn't get a working archive.

---

### Post by matt_symes on 2012-02-23
Hi

Slax can be used to check an ext4 filing system. You can aso create a bootable USB for it.

I have just used multisystem to create a bootable USB with it (I have been meaning to do that for ages on my rescue USB stick so thankyou for the prompting) but the other methods should work.

A fsck from Slax may fix the issue.

Kind regards

---

### Post by kurja on 2012-02-25
Booted slax, ran fsck, problem solved!!!!

---

