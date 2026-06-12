---
title: "`fdisk -l` = Random Order For Each Reboot | Screws Up /etc/fstab"
date: 2010-12-06
forum: General Help
---

### Post by switchrodeo720 on 2010-12-06
**_Problem:_** Each time I reboot my machine, my hard disks use different devices. This means that my /etc/fstab mappings don't match and I have to manually edit my fstab file and remount my drives.

I manually edit the /etc/fstab file to mount my drives, so I was really confused when I saw this happening but I cannot figure out why. Here is my fstab file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a2b6dc33-8655-42ed-92c4-e1a887000d3d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8c7cfbaf-cf8d-4232-9188-7d6aee66251e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /media/1500GB   auto    defaults        0       0
/dev/sdb1       /media/300GB    auto    defaults        0       0
/dev/sdc1       /media/1000GB   auto    defaults        0       0
```

I realize that this problem can be avoided by using the UUID for each drive, rather than the /dev/.... device label. However, I'm concerned because this hasn't ever happened to me before except when I've added/removed drives so I'm hoping that this isn't a symptom of a failing hard disk or something.

I hope that someone has had a similar experience and can shed some light on what I'm seeing.

Thanks in advance.

---

### Post by shoot2kill on 2010-12-06
Im afraid i cant help with the problem of why, and it seems very strange that it re-orders your partitions.

what other drives are you using? (sudo fdisk -l) and how are they configured (hardware/bios)

however, you are right in using UUID's. this will save changing the fstab in future.

---

### Post by efflandt on 2010-12-06
For speed, things are done simultaneously during boot, which is why drives do not necessarily always end up in the same order.  So it is best to use UUID's in fstab (like your / is mounted) instead of /dev/sda1, etc. so Linux can find them regardless of drive order.

To list UUID's of partitions simply do **sudo blkid**

---

### Post by sisco311 on 2010-12-06
EDIT: efflandt beat me to it & his explanation is much clearer.


> **switchrodeo720 said:**
> 
However, I'm concerned because this hasn't ever happened to me before except when I've added/removed drives so I'm hoping that this isn't a symptom of a failing hard disk or something.


It's not. 

From the [Arch Wiki]("https://wiki.archlinux.org/index.php/Udev"):
> udev loads kernel modules by utilizing coding parallelism to provide a potential performance advantage versus loading these modules serially. The modules are therefore loaded asynchronously. The inherent disadvantage of this method is that udev does not always load modules in the same order on each boot. If the machine has multiple block devices, this may manifest itself in the form of device nodes changing designations randomly. For example, if the machine has two hard drives, /dev/sda may randomly become /dev/sdb. See below for more info on this.

---

### Post by switchrodeo720 on 2010-12-06
I appreciate all the replies. I comforted to know that this isn't a sign of disaster. I'll set up the uuids in my fstab as the solution.

Thanks again to those who responded.

---

### Post by switchrodeo720 on 2010-12-07
Again, thanks to everyone who responded. I thought I would post my solution and method for those who may read this in the future...

**_Solution: _**

**_Step 1:_** Open your fstab.
```
sudo nano /etc/fstab
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
# / was on /dev/sda1 during installation
UUID=a2b6dc33-8655-42ed-92c4-e1a887000d3d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8c7cfbaf-cf8d-4232-9188-7d6aee66251e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /media/1500GB   auto    defaults        0       0
/dev/sdb1       /media/300GB    auto    defaults        0       0
/dev/sdc1       /media/1000GB   auto    defaults        0       0
```

**_Step 2:_** Get the UUIDs for my hard disks.

```
sudo blkid
```

This is the result for my machine using the command above.

```
/dev/sdd5: UUID="8c7cfbaf-cf8d-4232-9188-7d6aee66251e" TYPE="swap" 
/dev/sda1: LABEL="1500GB" UUID="63414f8e-6896-430e-857a-e40430a806a3" TYPE="ext2" 
/dev/sdc1: LABEL="1000GB" UUID="bf5c7e3e-636f-438e-bac7-510c64c6ff22" TYPE="ext4" 
/dev/sdb1: LABEL="300GB" UUID="b42f8e41-5b2d-42d8-a4af-32ed5fff3732" TYPE="ext4" 
/dev/sdd1: UUID="a2b6dc33-8655-42ed-92c4-e1a887000d3d" TYPE="ext4" 
```
[B][U]
Step 3:[/U][/B] Grab the UUIDs from the last step and merge them into your fstab file.

Here is what my final file looks like:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a2b6dc33-8655-42ed-92c4-e1a887000d3d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8c7cfbaf-cf8d-4232-9188-7d6aee66251e none            swap    sw              0       0
UUID=63414f8e-6896-430e-857a-e40430a806a3       /media/1500GB   auto    defaults        0       0
UUID=b42f8e41-5b2d-42d8-a4af-32ed5fff3732       /media/300GB    auto    defaults        0       0
UUID=bf5c7e3e-636f-438e-bac7-510c64c6ff22       /media/1000GB   auto    defaults        0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
[B][U]
Last notes:[/U][/B] After saving your new fstab file you can either reboot to mount your drives, or you can run the following command to mount them all right now:

```
sudo mount -a
```

---

