---
title: "My SWAP is AWOL"
date: 2012-06-17
forum: General Help
---

### Post by taylorkh on 2012-06-17
After MUCH configuration, many Clonezilla backups and a couple of restores to back up a step, I have my Ubuntu 12.04 classic gnome install working 98% to my liking. I have noticed that upon bootup a message flashes by just before the login screen. Today it stayed resident long enough for me to read some of it. It said something to the effect > Unable to ... ./dev/sda5 /dev/sda5 is my swap partition. Upon investigation I found...

System Monitor shows me that swap is not available
fdisk shows me that sda5 seems to be there OK> ken@taylor13:~$ sudo fdisk -l
[sudo] password for ken: 

Disk /dev/sda: 16.0 GB, 16013942784 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31277232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004c3d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    30000000    14998976+  83  Linux
/dev/sda2        30000001    31277231      638615+   5  Extended
/dev/sda5        30002049    31277231      637591+  82  Linux swap / Solaris
and fstab seems to be pointing to it> ken@taylor13:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    discard,errors=remount-ro 0       1
/dev/sda5        none            swap    sw              0       0
I did remove UUIDs because during my installing, testing, reinstalling, testing etc. I made the mistake of repartioning during one of the installs. When I restored the Clonzilla image of /dev/sda1 it complained about the UUID not being found (but booted in any event - ataboy fro the developers on that).

I see nothing in the logs regarding /dev/sda5. I am scratching my head on this one.](*,) Any ideas or advice?

TIA,

Ken

---

### Post by wilee-nilee on 2012-06-17
Install gparted and take a look at it.

---

### Post by taylorkh on 2012-06-17
Thanks wilee-nilee,

I have been doing a little more investigation. I tried > sudo swapon -a
swapon: /dev/sda5: read swap header failed: Invalid argumentI am now booting the PC from a USB live drive and will delete and recreate the partition with fdisk. Did that, did not work. Deleted the partition and the extended partition, created a primary partition 2 and set to swap. Edited /etc/fstab.  Still did not work.

A search on the swapon error message found some discussion on a Fedora forum. A recommendation was to run mkswap. I did this and got an error > warning: don't erase bootbits sectors (dos partition detected). Use -f to force.I don't know what a bootbit is but I know what a hammer is. So I forced it and swapon now works! 

A reboot to test and I am swappin' :D Well not really, I just upgraded my little netbook to 2 GB an with nothing running it has not gone to swap. But swap is available.

Thanks again,

Ken

---

