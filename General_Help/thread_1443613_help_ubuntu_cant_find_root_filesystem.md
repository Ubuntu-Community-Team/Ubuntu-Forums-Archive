---
title: "help ubuntu cant find root filesystem"
date: 2010-03-31
forum: General Help
---

### Post by Morten ML on 2010-03-31
Hi people

I have gladly been running ubuntu for about a year and now i have run into a problem i cannot seem to fix - therefore this post.

**My problem**
I have a dualboot win7 ubuntu 9.10 desktop asus eee1005ha. When booting into Ubuntu i get an error saying that the root file system can not be found.

**What seems to have coursed the problem**
I booted the system and forgot the plug in the external monitor. I therefore selected reboot (before logging in) and plugged in the external monitor. and there the problem was.

**What I need**
I need some data from ubuntu. - I do not care if i have to reinstall as long as I can get the data. (3 weeks of work and feel free to call me stupid for not taking backup but ubuntu just seemed so stable ;) )

**What I have tried**
I have looked at some posts about this issue:

[http://ubuntuforums.org/showthread.php?t=1327197&highlight=ubuntu+find+root+filesystem]("http://ubuntuforums.org/showthread.php?t=1327197&highlight=ubuntu+find+root+filesystem")
[http://ubuntuforums.org/showthread.php?t=887895&highlight=Unable+boot+problem+%28no+active+partition%29]("http://ubuntuforums.org/showthread.php?t=887895&highlight=Unable+boot+problem+%28no+active+partition%29")
[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")
etc.

I have succesfully booted from a live cd... but I cannot mount my drives.

gparted can see the partion but i cannot mount it from there - i can only delete it.

**Outputs**

```
sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb5bd2b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         477     3831471   82  Linux swap / Solaris
/dev/sda2             478       18243   142705395    5  Extended
/dev/sda3   *       18244       30401    97659135    7  HPFS/NTFS
/dev/sda5             478       18243   142705363+  83  Linux

```

```
ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2010-03-31 11:48 5EE8A0A6E8A07DC1 -> ../../sda3
lrwxrwxrwx 1 root root 10 2010-03-31 12:07 bc092a26-fb6e-4de8-9c21-2945011ad6cd -> ../../sda1

```

```
sudo grub-install /dev/sda5
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

**Please help**
any help would be greatly apreciated - as stated I do not care if it is "just" getting the data or restoring my system.

---

### Post by Morten ML on 2010-03-31
I found a way to see the data and it is not that deficult.

I found the solution in this thread:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8273955]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8273955")

The answer was found in the bottom of page 1 - posted by louieb.

```
sudo mkdir /mnt/z
```

Here is what louieb wrote:
```
sudo mount -t ext3 /dev/sda1 /mnt/z
```

And here is what I wrote:
```
sudo mount -t ext4 /dev/sda5 /mnt/z
```

And now the filesystem can be found in /mnt/z. 

I thought i might have missed a easy way to solve this, but i didnt think it would be so easy. I posted the solution so other newbies can make use of it. And maybe this should have been posted in completely newbies topic instead. feel free to move it if you are a moderator. 

Thanks for a great OS and for a forum that makes it easy to correct errors.

---

