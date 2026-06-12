---
title: "can't create partitions"
date: 2010-05-31
forum: General Help
---

### Post by ardll on 2010-05-31
hello,

i've followed the guides on the forums for creating new partitions using fdisk but I can;'t seem to create a new partition, after I (thought) i had created two new 70 gb partitions then rebooted after applying the new table I'm still just left with the following:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008947b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       19458   156039169    5  Extended
/dev/sda5              32       19458   156039168   8e  Linux LVM

I've know when I ran the ubuntu server setup I created a new 20 gb partition which I think the OS went on :confused: all i want to do now is use the rest of the drive to store files on to which can be accessed via the network

to be honest im actually confused whats the difference between 
/dev/sda2              32       19458   156039169    5  Extended
and
/dev/sda5              32       19458   156039168   8e  Linux LVM

---

### Post by srs5694 on 2010-05-31
Your existing partitions fill all available disk space, or as close to it as I can make out given the cylinder numbering used by default in fdisk. Thus, you can't create any new partitions. To do so, you'd need to delete or resize at least one partition.

An extended partition (type code 0x05 or 0x0f) is a placeholder for one or more logical partitions. This is an ugly workaround to a very very old limitation in the Master Boot Record (MBR) partitioning system used on most hard disks.

A Logical Volume Management (LVM) partition holds logical volumes, which are named partition-like structures that can be created, deleted, and resized much like files, without your having to worry about which specific sectors they occupy. LVM is a more advanced system than normal partitions, and using LVM can be very beneficial if your disk structures change frequently, if you want to create a single filesystem that's larger than any one disk you own, or for various other purposes. To manipulate logical volumes, though, you need to use tools other than fdisk. These tools have names that begin with pv, vg, or lv, as in lvcreate or lvresize. Alternatively, you can use a GUI LVM tool, such as system-config-lvm or kvpm.

Your system is set up to use LVM -- or at least, your /dev/sda5 partition is marked as an LVM partition. (It might or might not contain the basic LVM data structures.) If you want to use LVM, you must use the various LVM utilities to create logical volumes for Ubuntu, then install Ubuntu to those. It sounds like you're new to Linux, though, and I can't really recommend that new Linux users attempt to use LVM; although LVM is very flexible and can simplify certain advanced operations, it's complex enough that it's hard for new users to deploy it. This is especially true in Ubuntu, which provides poor install-time LVM support. Your best course of action is probably to completely redo the partitioning scheme. If you're installing Ubuntu from scratch, you should be able to tell the installer to use the whole disk; or you can choose a custom partitioning option and set up one or more Ubuntu partitions in the space now occupied by the ones you've got.

---

### Post by ardll on 2010-05-31
thanks for your reply, ubuntu has already been installed and unfortunately I'm now connecting to the machine via SSH on a windows pc and doing everything from there; there is no monitor or cd drive attached to it, what is the easiest way for me to now make use of the rest of the drive to store files on?

---

### Post by srs5694 on 2010-06-01
Please post the output of the following commands:

```

sudo df -h
sudo vgdisplay
sudo lvdisplay

```

---

