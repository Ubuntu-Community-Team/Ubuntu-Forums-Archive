---
title: "Dual boot problem regarding ubuntu10.04 and windows vista"
date: 2012-01-20
forum: General Help
---

### Post by techieyodha on 2012-01-20
i have installed ubuntu 10.04 on my computer. Later on i needed to install windows vista . so, i installed windows vista. vista was working fine. But then i can't boot in to my ubuntu10.04. so i entered live cd and updated my grub. after Restarting i could not get the windows vista back. once again i inserted windows vista cd and tried to repair from cd (vista cd)  and even from command prompt using x:\bootrec\rebuildbcd.
  But it says that there is no windows installation.

so my problem is (1)I could not boot up windows vista which i need to boot urgently because i have to do my projects
(2)i did not get boot up list for different operating systems while starting the system.
              plz, guys  help me out with ur solutions as soosn as possible

---

### Post by muteXe on 2012-01-20
So at the moment you can log into ubuntu?

if so, open a terminal and type 
```

sudo fdisk -l

```

that's a small L, not a 1.
paste results back here.

This is just initially to establish you still have a vista partition..

edit: if you cant boot into your linux, boot from your live cd

---

### Post by techieyodha on 2012-02-18
hey dude sorry 2 contact u late. actually my NIC card malfunctioned.so i have to set up a new one.
i booted with ubuntu live cd and got the following result.


[B][COLOR=#000000][FONT=Verdana]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Disk /dev/sda: 320.1 GB, 320072933376 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]255 heads, 63 sectors/track, 38913 cylinders[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Disk identifier: 0xf96673cc[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]   Device Boot      Start         End      Blocks   Id  System[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]/dev/sda1               2       15298   122871937    f  W95 Ext'd (LBA)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]/dev/sda2   *       15298       26772    92160000    7  HPFS/NTFS[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]/dev/sda3           26772       38914    97528832    7  HPFS/NTFS[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]/dev/sda5               2        5226    41969781    7  HPFS/NTFS[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]/dev/sda6            5227       15298    80902144   83  Linux[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ubuntu@ubuntu:~$ [/FONT][/COLOR][/B]

---

