---
title: "VMware 8 Physical Drive"
date: 2011-12-20
forum: General Help
---

### Post by blackhex666 on 2011-12-20
I want to add a physical harddrive but i get an error

Oke so the error is this:
```

Failed to load partitions for device /dev/sda: Insufficient permission to access file
```How do i get there?:
Edit virtual machine settings > Add New device > Hard Disk > Use a physical disk (for advanced users) > selectez Device : /dev/sda/ >
 Usage: Use individual partition > Next > and boom a nice erorr with a red !


My HDD is mounted on D
```

blackhex@blackhex-desktop:~/vmware$ ls -l
total 40
drwxrwxrwx 3 blackhex blackhex 4096 2011-12-20 15:17 BackBox Ubuntu
drwxrwxrwx 3 blackhex blackhex 4096 2011-12-20 15:17 Caine 2.6.x kernel
drwxrwxrwx 3 blackhex blackhex 4096 2011-12-20 15:17 DefT 2.6.x kernel
drwxrwxrwx 4 blackhex blackhex 4096 2011-12-20 15:17 GnackTrack Ubuntu
drwxrwxrwx 4 blackhex blackhex 4096 2011-12-20 15:18 Machine
drwxrwxrwx 3 blackhex blackhex 4096 2011-12-20 15:17 NetSecL OpenSUSE
drwxrwxrwx 2 blackhex blackhex 4096 2011-12-20 12:44 SANS504LinuxV0209
drwxrwxrwx 3 blackhex blackhex 4096 2011-12-20 15:17 Wiflax Slax 2.6.x kernel
drwxrwxrwx 4 blackhex blackhex 4096 2011-12-20 15:18 Windows XP Professional
drwxrwxrwx 4 blackhex blackhex 4096 2011-12-20 15:17 WinXP BaseZero
blackhex@blackhex-desktop:~/vmware$ cd
blackhex@blackhex-desktop:~$ cd /media
blackhex@blackhex-desktop:/media$ ls -l
total 28
drwxr-xr-x 1 blackhex blackhex 20480 2011-12-20 08:46 D
drwxr-xr-x 2 root     root      4096 2011-12-18 14:05 hdd
drwxr-xr-x 2 blackhex blackhex  4096 2011-12-20 11:02 mount1
blackhex@blackhex-desktop:/media$ ls -l
total 28
drwxr-xr-x 1 blackhex blackhex 20480 2011-12-20 08:46 D
drwxr-xr-x 2 root     root      4096 2011-12-18 14:05 hdd
drwxr-xr-x 2 blackhex blackhex  4096 2011-12-20 11:02 mount1

```blackhex@blackhex-desktop:/media$:

---

