---
title: "Chroot Fails"
date: 2012-10-12
forum: General Help
---

### Post by Xplorer4x4 on 2012-10-12
I have a ubuntu server. I needed to modify the network config so I did but when restarting the network interface it refused to respond. OVH offers a Rescue mode. After botting to rescue mode you have to mount your hard drive, chroot the mountpoint. I did this before on a on-raid box like so:
```
mkdir /mymount && mount /dev/sda1 /mymount
chroot /mymount
mount /dev/sda2 /home
```
Now I had a box with RAID mode enabled. I have identified /dev/md3 as the mount point for the RAID since this partition is the size of both hard drives. So I try:
```
mkdir /mymount && mount /dev/md3 /mymount
chroot /mymount
mount /dev/sda9 /home
```
But when I run chroot, I get this:
```
root@rescue:~# chroot /mymount
chroot: failed to run command `/bin/bash': No such file or directory
```
If I run mount I see the partition is properly mounted. I can cd in to /mymount but not chroot. If I cd in to /mymount I see users home dirs so I now I have the right partition.

How come I can not chroot the active mount point?

---

### Post by dcstar on 2012-10-12
> **Xplorer4x4 said:**
> I have a ubuntu server. I needed to modify the network config so I did but when restarting the network interface it refused to respond. OVH offers a Rescue mode.
..........
How come I can not chroot the active mount point?

You must boot the same architecture. If you have a 64-bit system then you must boot a 64-bit rescue disk to use chroot.

---

### Post by Xplorer4x4 on 2012-10-12
OVH handles that. I double checked and the rescue environment is 64 bit.
```

root@rescue:/dev# uname -mrsn
Linux rescue.ovh.net 3.2.2-xxxx-std-ipv6-64 x86_64

```
And the server is running Precise 64bit.

---

### Post by dcstar on 2012-10-12
> **Xplorer4x4 said:**
> OVH handles that. I double checked and the rescue environment is 64 bit.
```

root@rescue:/dev# uname -mrsn
Linux rescue.ovh.net 3.2.2-xxxx-std-ipv6-64 x86_64

```
And the server is running Precise 64bit.

Then look in the mountpoint for valid files like /bin/bash.

---

### Post by Xplorer4x4 on 2012-10-12
> **dcstar said:**
> Then look in the mountpoint for valid files like /bin/bash.

What do you mean? For what it is worth I can see that chroot is available in rescue mode.
```
root@rescue:/# chroot --version
chroot (GNU coreutils) 8.5
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by Roland McGrath.
root@rescue:/# 

```

---

### Post by Wim Sturkenboom on 2012-10-12
For a chroot'ed environment, you need to copy all programs that you possibly want to use. So you need e.g. a /bin directory in /dev/md3 and it should contain bash. Also check with ldd which libraries might be required.

---

### Post by Xplorer4x4 on 2012-10-12
My hard disk contains a fully working Ubuntu Server install other then network configuration file so of course it has bash installed. All I need to do is chroot the disk so I can modify the network configuration file.

---

### Post by Wim Sturkenboom on 2012-10-12
> **Xplorer4x4 said:**
> My hard disk ...Which one? /dev/md3? If so, I don't know.

---

### Post by Xplorer4x4 on 2012-10-12
> **Wim Sturkenboom said:**
> Which one? /dev/md3? If so, I don't know.

Considered this is what I am trying to mount to fix the network config file...yes. And you don't know what exactly?

---

### Post by Xplorer4x4 on 2012-10-12
> **Wim Sturkenboom said:**
> For a chroot'ed environment, you need to copy all programs that you possibly want to use. So you need e.g. a /bin directory in /dev/md3 and it should contain bash. Also check with ldd which libraries might be required.

Got me thinking, so I checked fdisk and it made me suspect I hate the data storage area rather then the root filesystem, so I switched to /dev/md1 and it worked right away. 

The last mount command failed complaining baout not specifying the filesystem, which even if I did, it refused to mount. Edited network/interfaces and rebooted and had a working machine. Thanks for atleast getting my mind contomplainting this and finding the proper partition.

---

### Post by Wim Sturkenboom on 2012-10-12
> **Xplorer4x4 said:**
> Got me thinking, :lolflag:

Please mark your thread as solved using the thread tools just above the first post on this page.

---

