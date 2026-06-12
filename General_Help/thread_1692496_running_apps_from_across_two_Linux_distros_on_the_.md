---
title: "running apps from across two Linux distros on the same disk"
date: 2011-02-21
forum: General Help
---

### Post by rajn on 2011-02-21
Hi,
I really do not know how to phrase this question properly. I am quite unaware of the PC jargon. But I have Ubuntu as the main OS and Mandriva is the second OS on the same hard disk. The boot loader is the Ubuntu. When I want to switch to Mandriva, on boot up I press Shift and then select the kernel.

However, if I am on Ubuntu and want to run an application which resides on Mandriva, how do I do that? My fstab file does not even mention Mandriva. However, the file system does show up that file and I can open any files I need by clicking on  GUI "Places". But when I try to run any of its applications by clicking the appropriate file on its /bin file nothing happens. A pop-up window briefly flashes and disappears. So my questions are:

1. First how can I change directory so that I am on Mandriva. Can' cd ...something'  take me to that file because I see it in "Places" as a 36Gb file system?

2. How can I run an application which resides on that file system e.g., R or Octave which I do not have installed on Ubuntu, without rebooting into Mandriva.

3. Can I do this from command line.

4. And finally, can I do the same from Mandriva i.e., access Ubuntu from it.

I did read quite a bit about mounting files and fstab, but the fstab does not show the file system I am talking about. These are the outputs from Ubuntu os.

fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=60381912-ff90-4d8b-ae4c-4089fed79ac1 /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext4    defaults        0       2
# /home was on /dev/sda3 during installation
UUID=00277ef9-d90f-4dec-8a57-a12bf1176191 /home           ext4    defaults        0       2
# /opt was on /dev/sda8 during installation
UUID=99efa890-4976-4578-b654-4f6960fd6789 /opt            ext4    defaults        0       2
/dev/sda5       /tmp            ext4    defaults        0       2
# /usr was on /dev/sda6 during installation
UUID=9e2a1089-de25-438c-8ea4-0e2fbc4f7759 /usr            ext4    defaults        0       2
# /usr/local was on /dev/sda9 during installation
UUID=0779acac-45b6-44bc-8ce1-31440a813c6a /usr/local      ext4    defaults        0       2
# /var was on /dev/sda7 during installation
UUID=061b266a-ec77-44dd-93d0-8463fb1cffff /var            ext4    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=33c0489a-26e9-4a3d-ab2c-ae1a9596b6af none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

fdisk -l:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023100

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         244     1951744   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             244         851     4882432   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3             851        1459     4882432   83  Linux
/dev/sda4            1459        9729    66429562+   5  Extended
/dev/sda5            1459        1520      487424   83  Linux
/dev/sda6            1520        2128     4881408   83  Linux
/dev/sda7            2128        2371     1951744   83  Linux
/dev/sda8            2371        2614     1951744   83  Linux
/dev/sda9            2614        3222     4881408   83  Linux
/dev/sda10           3222        3465     1951744   82  Linux swap / Solaris
/dev/sda11           3466        5032    12586896   83  Linux
/dev/sda12           5033        5541     4088511   82  Linux swap / Solaris
/dev/sda13           5542        9729    33640078+  83  Linux

I think sda11,12 and 13 belong to the Mandriva system.
Thanks

---

### Post by rajn on 2011-02-23
Hi, 
Bump anyone?
I thought this should be an easy one for the Linux gurus....

---

### Post by oldfred on 2011-02-23
You are dual booting. So you have to boot each separately. Why cannot you install the same app in both systems? You can share data if set into a separate partition.

I thought Mandriva is enough different that its apps may not work without recompiling for Debian anyway.

If your system has the horsepower & memory you could install it in virtual system like VirtualBox.

You might be able to chroot into system, but I only use that for repairs, not actually running system.

---

