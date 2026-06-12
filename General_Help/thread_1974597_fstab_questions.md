---
title: "fstab questions"
date: 2012-05-06
forum: General Help
---

### Post by Prescilla on 2012-05-06
Good day everyone.

I just have a few questions regarding the fstab file.
Here's the contents of my fstab file:

prescilla@prescilla:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=870a8144-7a6b-4fad-8190-cf7c9ffe598b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=6a813473-a00c-4b1c-9dbf-258aa076f3c2 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=4289df24-5d83-4d6e-84e7-8492031900fe none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Here are my questions.
1. Before I upgraded to Precise Pangolin, the file system column of the fstab lists the devices with sda1, sda2, etc not with UUID.
I prefer to view devices with sda1 labels not UUID. Is there a way to do that?
2. I have two other partitions but they are not listed in the fstab file. How do I add them to the fstab file.

Here's a view of my partitions with GParted:
[IMG]http://img33.imageshack.us/img33/4430/42942385.png[/IMG]
By [prescilla_c](http://profile.imageshack.us/user/prescilla_c) at 2012-05-03

---

### Post by JRV on 2012-05-06
1 - All you have to do is change the "UUID=870a8144-7a6b-4fad-8190-cf7c9ffe598b" back to "/dev/sda1" for /.
The comment above the UUID line tells you what to change it to.

---

### Post by amosek on 2012-05-06
Hi

Just add to the bottom of /etc/fstab

/dev/sda5 /media/DATA    ntfs defaults 0 0
/dev/sda6 /media/MOVIES  ntfs defaults 0 0

Then run sudo mount -a to mount them

You can also get rid of UUIDs .. just replace UUID=xxxx with /dev/sdX .. I just don't see a point of doing this

Hope it helps

---

### Post by Lars Noodén on 2012-05-06
As JRV points out, it is the comment lines above the fstab entries that tell you what the old devices were without the UUID.  You can also see what is currently mounted by using [mount](http://manpages.ubuntu.com/manpages/precise/en/man8/mount.8.html)

But before you make any changes, be sure to make a copy of fstab to restore from if you happen to make a mistake.

---

### Post by SeijiSensei on 2012-05-06
Mounting by UUID is preferred because it is invulnerable to things like inserting a USB external drive before booting.  Depending on how the BIOS handles multiple devices, /dev/sda will usually remain the same in nearly all cases, but not always.  UUIDs are especially important for devices other than the main boot drive.  A second hard drive in your machine might be /dev/sdb without an external device plugged in, but become /dev/sdc if you plug in a USB pendrive before booting.  With multiple external devices, say a pendrive and a large external drive, the assignments can be even more mutable.

---

### Post by sudodus on 2012-05-06
> **SeijiSensei said:**
> Mounting by UUID is preferred because it is invulnerable to things like inserting a USB external drive before booting.  Depending on how the BIOS handles multiple devices, /dev/sda will usually remain the same in nearly all cases, but not always.  UUIDs are especially important for devices other than the main boot drive.  A second hard drive in your machine might be /dev/sdb without an external device plugged in, but become /dev/sdc if you plug in a USB pendrive before booting.  With multiple external devices, say a pendrive and a large external drive, the assignments can be even more mutable.
+1
But you can still have nice human-readable names of your partitions using ***labels***. It is easy to assign labels to your partitions with ***gparted***. If you want to check the labels you can use gparted or the terminal command ```
sudo blkid
``` The labels will be used as names of the mounted partitions, so it is easy to identify them in the file browser etc.

---

### Post by Morbius1 on 2012-05-06
Agree with both SeijiSensei and sudodus and gparted is already showing you what the partition labels are. For example to auto mount the ntfs partition on boot in fstab you have 3 options:

The old way:
```
/dev/sda5 /media/DATA ntfs defaults,nls=utf8,uid=1000 0 0
```The "best" way:
```
UUID=0424FBBE24FBB0B2 /media/DATA ntfs defaults,nls=utf8,uid=1000 0 0
```[COLOR=Blue]*Note: your UUID will be different.*[/COLOR]

The label way ( better than the old way - just make sure you don't have the same labels on other partitions ):
```
LABEL=DATA /media/DATA ntfs defaults,nls=utf8,uid=1000 0 0
```

---

### Post by Prescilla on 2012-05-07
Got it. Thanks for all your help.

---

### Post by Prescilla on 2012-05-07
> **Morbius1 said:**
> Agree with both SeijiSensei and sudodus and gparted is already showing you what the partition labels are. For example to auto mount the ntfs partition on boot in fstab you have 3 options:

The old way:
```
/dev/sda5 /media/DATA ntfs defaults,nls=utf8,uid=1000 0 0
```The "best" way:
```
UUID=0424FBBE24FBB0B2 /media/DATA ntfs defaults,nls=utf8,uid=1000 0 0
```[COLOR=Blue]*Note: your UUID will be different.*[/COLOR]

The label way ( better than the old way - just make sure you don't have the same labels on other partitions ):
```
LABEL=DATA /media/DATA ntfs defaults,nls=utf8,uid=1000 0 0
```
This helped me understand a lot.
Thank you.
How do I marked this as SOLVED?

---

### Post by JRV on 2012-05-07
Click on thread tools, it's red and on the top of the page.

---

### Post by Prescilla on 2012-05-08
> **JRV said:**
> Click on thread tools, it's red and on the top of the page.
Thanks! Got it!

---

