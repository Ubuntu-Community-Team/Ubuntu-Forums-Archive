---
title: "Mounting HDDs at startup"
date: 2010-03-17
forum: General Help
---

### Post by wrix on 2010-03-17
Hello, I am a new user of Ubuntu. I have a portable hard disk and two fixed hard disks. If I connect my portable hard disk before booting the system and then boot, I get it mounted on /media. But this does not happens to my other partitions. I am unable to get the fact. Hope anyone can help me in this regards. Thanks in advance.

---

### Post by Zayfox on 2010-03-17
Have you tried unplugging them, and typing ```
sudo modprobe usb_storage
``` into terminal, then plugging them back in?

---

### Post by aeiah on 2010-03-17
you need to create directories for them in /media (or anywhere else really) and put mounting details in /etc/fstab

first you should mount them manually on the command line (this isnt persistent) so you can identify which drive is which. your drives are listed as unmounted devices in /dev/. if you do ```
ls /dev/sd*
``` in a terminal you should get a list of all your devices and partitions.

its just a matter of issueing a command like this to mount a drive temporarily:
```

sudo mount /dev/sda1 /media/drivefolder/

```

there's loads of documentation for mounting drives permanently on boot through editing the fstab file, with loads of examples for different file systems.

---

### Post by egalvan on 2010-03-17
Internal drives are not normally mounted to /media.

is there a reason you  want/need these internal drives mounted to /media?

In any case...
for starters, show us fstab...

```
gedit /etc/fstab
```

and paste the contents here (wrap it in code tags, please.)

also,

```
sudo fdisk -l
```

(that's a lower-case L, not the numeral one)

and paste the contents here (wrap it in code tags, please.)

---

### Post by wrix on 2010-03-17
This is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=2c42cb86-9219-4477-a373-db2c8fcd4e8b /               xfs     relatime        0       1
# swap was on /dev/sdb5 during installation
UUID=d1b0309b-e744-4f6d-9354-5e9906de9c25 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

And this is the the result of fdisk -l:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005e6f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13054   104856223+  83  Linux
/dev/sda2           13055       19457    51432097+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61806180

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9240    74220268+  83  Linux
/dev/sdb2   *        9266       19458    81863680   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sdb3            9241        9265      200812+   5  Extended
/dev/sdb5            9241        9265      200781   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by Wardje on 2010-03-18
> **egalvan said:**
> Internal drives are not normally mounted to /media
All my internal drives mount there automatically (when I open them from Places or Computer), except for root of course. Where might they mount for you? :o

---

### Post by dcstar on 2010-03-18
> **Wardje said:**
> All my internal drives mount there automatically (when I open them from Places or Computer), except for root of course. Where might they mount for you? :o

All permanent non-system mounts should be outside of the Linux system folders - like /media - because **you** are using them for non-system purposes and may want to change system controlled defaults like permissions etc. Things mounted in /media are done by the system using its preferences.

All Linux system folders are assumed to be under the control of the system and allowing other things to access those folders can compromise security as well as operational stability.

If you have a drive for data then create you own folder called /data and mount it there - the name doesn't matter as long as it is **not** in a Linux system folder.

Using the command "sudo mkdir /whatever" isn't that tough to do.

---

### Post by Wardje on 2010-03-19
Oh like that, I misinterpreted egalvan's line. I thought he meant it isn't default behaviour on Ubuntu's side while he meant that it isn't advised to mount it there. :P

---

### Post by wrix on 2010-03-19
Can anyone give a simple answer to my questions please.....

---

