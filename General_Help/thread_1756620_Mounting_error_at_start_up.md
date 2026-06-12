---
title: "Mounting error at start up"
date: 2011-05-12
forum: General Help
---

### Post by layers on 2011-05-12
I get this error on startup, and I have to press ESC, mount -a, exit, in order to be able to boot up successfully.

```
one or more of the mounts listed in /etc/fstab cannot yet be mounted:
/: waiting for /dev/disk/by-uuid/4d817f08-6b0a-4216-a3f0-ad944e67989e
/tmp: waiting for (null)
/media/here: waiting for /dev/sda2
Press ESC to enter a recovery shell
```

I have this in fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=4d817f08-6b0a-4216-a3f0-ad944e67989e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=17cc3a91-c9c5-4ddb-b083-d4281a2bf995 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda2 /media/here vfat utf8,umask=000,uid=1000 0 2

```

and this in fdisk -l
```
ibo@ibo-laptop:~$ sudo fdisk -l
[sudo] password for ibo: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe64be64b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         134     1076323+  82  Linux swap / Solaris
/dev/sda2            8925       19457    84606322+   c  W95 FAT32 (LBA)
/dev/sda3   *         135        8924    70605675   83  Linux

Partition table entries are not in disk order

```

Does anyone know how to fix this?

---

### Post by matt_symes on 2011-05-12
Hi

Open a terminal and type

```
sudo blkid -c /dev/null
```

Please post the results back here. This will tell us the partitions UUIDs.

Kind regards

---

### Post by layers on 2011-05-12
```
/dev/sda1: UUID="17cc3a91-c9c5-4ddb-b083-d4281a2bf995" TYPE="swap" 
/dev/sda2: LABEL="" UUID="E083-1B57" TYPE="vfat" 
/dev/sda3: UUID="4d817f08-6b0a-4216-a3f0-ad944e67989e" TYPE="ext4" 
```

---

### Post by matt_symes on 2011-05-12
Hi

Your UUIDs look fine. Is this a new install ?

You could increase the root delay on the kernel command line.

```
rootdelay=90
```Where 90 is the number of seconds to wait before timing out. You will have to update grub for this. Post back if you need instructions.

You can test it from the grub command line.

Kind regards

---

### Post by layers on 2011-05-12
Did something, but it did not work. Was this shat you had in mind, matt_symes?

```
sudo mousepad /etc/default/grub
```changed from this
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
**GRUB_TIMEOUT="10"**
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```to this
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
**GRUB_TIMEOUT="90"**
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```and then followed with geub update

---

### Post by matt_symes on 2011-05-12
Hi

This is what i meant.
[FONT=monospace]
[/FONT]```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
**GRUB_TIMEOUT="10"**
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootdelay=90"**
GRUB_CMDLINE_LINUX=""
```

```
sudo update-grub
```

Hopefully that will work for you.

Kind regards

---

### Post by layers on 2011-05-12
right, sorry I missed that.
And how would I test without restarting?

---

### Post by matt_symes on 2011-05-12
Hi

> And how would I test without restarting?I think restarting might be the only way to test it properly.

Even then i am not sure if it will fix your issue. It will give a longer timeout for the drive to become ready though and i think that may be the problem your are having.

Is this a new install ?

Kind regards

---

### Post by layers on 2011-05-12
Didn't work.
It was a new install (what is the other option?), and this problem occurred recently.

---

### Post by layers on 2011-05-12
Mmm... commenting out the last line in fstab got rid of the issue.

```
#/dev/sda2 /media/here vfat utf8,umask=000,uid=1000 0 2
```

Why? I like it automounted.

---

### Post by matt_symes on 2011-05-12
Hi

> **layers said:**
> Mmm... commenting out the last line in fstab got rid of the issue.

```
#/dev/sda2 /media/here vfat utf8,umask=000,uid=1000 0 2
```Why? I like it automounted.

Try using the UUID for that partition in fstab
[FONT=monospace]
[/FONT]```
**UUID=E083-1B57**  /media/here vfat utf8,umask=000,uid=1000 0 **0**
```
Replace the last 2 with a 0 as i have done above.

That might auto mount it at boot.

Kind regards

---

### Post by layers on 2011-05-12
thanks, that worked - it mounted and did not have the error. Now, next issue. :)

---

