---
title: "Fresh hdd not mounting - mtab error"
date: 2011-12-17
forum: General Help
---

### Post by drneolao on 2011-12-17
Having a bit of an odd problem.

I have Ubuntu 11.04 on a middle of the road computer (2.4Gh with 3Gb ram).

Installed a fresh drive (not new) that had been used in a different computer. Formatted it but when I go to mount it, it gives me this error:

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed

The odd thing is, the main drive (with the OS on it) is sdb1 (already mounted), but the fresh drive I'm trying to mount is listed as sd**a**1 in Disk Utility. Tried every option I could find in Disk Utility and tried pluging into different ports (SATA drives) and I keep getting the same error. It's like the machine is getting confused about which drive is which.

Suggestions?

---

### Post by matt_symes on 2011-12-17
Hi

Let's get some information about your setup.

Open a terminal and type

```
sudo fdisk -l
```

That's a small L after fdisk. Copy and paste the results back here between code tags like this

[noparse]```
output from fsidk
```[/noparse]

to get output like this

```
output from fsidk
```

Also post the output of 

```
cat /etc/mtab
```

It sounds to me like udev is trying to mount on sdb when sdb is already taken.

The drive you are trying to mount is an internal sata drive ?

Kind regards

---

### Post by drneolao on 2011-12-19
Output from fdisk:

```
Disk /dev/sda: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000deb54

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18936   152096768   83  Linux
/dev/sdb2           18936       19458     4191233    5  Extended
/dev/sdb5           18936       19458     4191232   82  Linux swap / Solaris
```sdb (160Gb) is the original disk that was the only one that was in there on installation (blank install, re-partition and format an older drive). sda (320Gb) is the new one that I just put in which does not want to mount (also re-partitioned and formatted).

Output from mtab:

```
/dev/sdb1 / ext4 rw,errors=remount-ro,user_xattr,commit=0 0 0
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
gvfs-fuse-daemon /home/leo/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=leo 0 0
```Tried again just now and still getting the same error... Not sure why, still getting the same error as in the first post, even though the new drive is sda.

---

### Post by matt_symes on 2011-12-20
Hi

First things first. Let's check you can mount it manually.

Open a terminal and type 

```
sudo mkdir /media/drive_a
```Enter your password. It will not be echoed to the screen.

Then type

```
sudo mount -t ext4 /dev/sda /media/drive_a
```Does it mount it ?

To unmount 

```
sudo mount /dev/sda
```Can you also post the output of

```
cat /etc/fstab
```Kind regards

---

### Post by drneolao on 2011-12-20
Hmm, still having issues.

Creating the directory was no problem (as expected), manual mount gave this error:

```
965P-DQ6:~$ sudo mount -t ext4 /dev/sda /media/drive_a
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```Output of fstab:

```
965P-DQ6:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=25e35384-19df-4c4b-afc4-1a81ef5fa370 none            swap    sw              0       0

```Interesting. It appears that mtab says the mounted drive (160Gb) is sdb but fstab seems to think it is sda...

I wonder if it affects it if the fresh disk that is going in might have had Linux installed on it previously? I don't think it did but I lost track of which disk had what on it. Though I would have assumed the clearing the partitions and re-formatting would have removed any old data.

It's also possible the disk may have a fault... not sure how to test that.

---

### Post by drneolao on 2011-12-22
I tried to get clever and manually mount the disk as sdc on /media/drive_b but that gave me an error as well... :(

---

### Post by matt_symes on 2011-12-25
Hi

Silly question but is the drive formatted ?

Kind regards

---

### Post by Morbius1 on 2011-12-25
For what it's worth:

[1] Run the following command to get the correct UUID number of all your partitions:
```
sudo blkid -c /dev/null
```[2] Then change this line in fstab:
>  /dev/sda1       /               ext4    errors=remount-ro,user_xattr 0       1To this - [COLOR=Blue]with the correct uuid number for that partition:[/COLOR]
>  UUID=[COLOR=Blue]f7927995-b098-42be-ada0-987857f5177a[/COLOR]       /               ext4    errors=remount-ro,user_xattr 0       1Your partitions have "flipped" ( sdb becomes sda ) which is why installers specify everthing by UUID today.

---

### Post by drneolao on 2011-12-26
@Matt: Hmm, maybe not so silly. It *should be formatted* since I  gave it that command and it comes up as a valid though un-mounted  partition. I might give it another format.

Output from blkid:
```
/dev/sda1: LABEL="New Volume" UUID="ca832f24-c763-4467-b521-daf4acb0564b" TYPE="ext4" 
/dev/sdb1: UUID="b8ba362f-db92-4324-89f4-a3c63d6d1a32" TYPE="ext4" 
/dev/sdb5: UUID="25e35384-19df-4c4b-afc4-1a81ef5fa370" TYPE="swap" 
```

*About to do the change, just posting to save data, then I'll edit with new info.***Yay! Fixed.** So by editing the fstab file and telling the specific UUID of the main drive, the second drive then mounted normally via System Settings > Disk Utility and selecting "Mount Drive".

Thank you both for your help! :D

---

