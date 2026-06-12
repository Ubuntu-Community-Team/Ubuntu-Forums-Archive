---
title: "recreate a home parition from scratch"
date: 2011-04-16
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-04-16
i had a hdd fail on me (serve me right for using one that was about 9 years old)
i was using 2 hdds my home drive failed i did not loose anything that is not replaceable except my time about 2 days of downlaoding a game ](*,)
anyway I am copying my system partition do a disk that supports SMART how do i make a new home partition with out making a new install?

---

### Post by Hedgehog1 on 2011-04-17
pqwoerituytrueiwoq,

Your current install (before the HDD died) was using the /etc/fstab file to identify the partition that carried the '/home' directory.

Here is a look at mine (your UUIDs will be different):

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda5 during installation
UUID=f2fd03c5-2835-415c-8448-75473daf624a  /                 ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=cb0c7226-150e-45ca-ba5c-2e161dc10f6a  none              swap  sw                   0  0  
# /home partition was /dev/sda7
**[COLOR="Red"]UUID=4aebc2c6-5984-47e3-b2ea-7fdfaf23343e  /home             ext4  nodev,nosuid         0  2[/COLOR]**
```

When you install your new disk, create a '/home' directory in a partition on it (most likely the partition will be the whole drive in your case).

Then, take the UUID of the new partition, and exchange it for the UUID in your /etc/fstab file that points to '/home'.

To edit the /etc/fstab file, do this:

```
gksudo gedit /etc/fstab
```

The Hedge

:KS

p.s. Here is a picture to help other readers follow this:

[IMG]http://img840.imageshack.us/img840/4129/laptophd.png[/IMG]

---

