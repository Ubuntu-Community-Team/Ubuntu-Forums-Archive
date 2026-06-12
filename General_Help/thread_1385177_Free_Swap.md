---
title: "Free Swap"
date: 2010-01-19
forum: General Help
---

### Post by eipapp on 2010-01-19
What am I missing ? I can't get my computer to hibernate. Each time I click on hibernate it begins to do so then just as quickly comes back into run mode. I tried various options from ideas presented in Ubuntu forums but always I get the message "not enough free swap" despite the fact that I've allocated 2Gb for a swap partition. FYI .. I have 512 Mb of ram.
Can anyone help or is this problem unsolvable ?

Thanks,
Bruce

---

### Post by audiomick on 2010-01-19
Are you sure that your swap is all mounted? And it is a partition, not a swap file?

Do
```
top
```
in the terminal to see if the swap is all there, and how much is being used.

To post the output back here, let it run for a couple of seconds, then do CTRL + Z to pause it, then copy this bit

```
top - 15:20:58 up  2:39,  2 users,  load average: 0.04, 0.05, 0.02
Tasks: 171 total,   1 running, 170 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7%us,  0.3%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4057984k total,  1383372k used,  2674612k free,   146896k buffers
Swap:  6257268k total,        0k used,  6257268k free,   675092k cached
```from up the top and paste it back here.

---

### Post by donaldhall on 2010-01-19
edit: nvm hahaha one above me is way better

---

### Post by eipapp on 2010-01-19
> **audiomick said:**
> Are you sure that your swap is all mounted? And it is a partition, not a swap file?

Do
```
top
```in the terminal to see if the swap is all there, and how much is being used.

To post the output back here, let it run for a couple of seconds, then do CTRL + Z to pause it, then copy this bit

```
top - 15:20:58 up  2:39,  2 users,  load average: 0.04, 0.05, 0.02
Tasks: 171 total,   1 running, 170 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7%us,  0.3%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4057984k total,  1383372k used,  2674612k free,   146896k buffers
Swap:  6257268k total,        0k used,  6257268k free,   675092k cached
```from up the top and paste it back here.

bruce@ubuntu:~$ top

top - 09:36:56 up 31 min,  2 users,  load average: 0.76, 0.96, 0.68
Tasks: 127 total,   1 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s): 24.6%us,  9.3%sy,  0.0%ni, 65.8%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:    508156k total,   496760k used,    11396k free,    86464k buffers
Swap:   262136k total,     8268k used,   253868k free,   150836k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2063 bruce     20   0  252m  49m  23m S  9.9 10.0   2:01.18 rhythmbox          
 1630 bruce     20   0  220m 7172 5932 S  8.6  1.4   1:14.35 pulseaudio         
 2091 bruce     20   0  526m 123m  31m S  7.6 24.9   5:04.85 firefox            
  891 root      20   0 49360  27m 8460 S  4.3  5.6   3:40.05 Xorg               
 2309 bruce     20   0 37252  12m 9604 S  2.6  2.5   0:00.79 gnome-terminal     
 2330 bruce     20   0  2468 1160  884 R  0.7  0.2   0:00.31 top                
  331 root       0 -20     0    0    0 S  0.3  0.0   0:03.23 loop0              
  992 root      20   0  3420 1140  972 S  0.3  0.2   0:00.82 hald-addon-stor    
 1691 bruce     20   0 17360 6436 5740 S  0.3  1.3   0:00.20 gnome-power-man    
    1 root      20   0  2532 1476 1128 S  0.0  0.3   0:01.53 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            

[1]+  Stopped                 top
bruce@ubuntu:~$

---

### Post by audiomick on 2010-01-19
This looks like the problem
Mem: [COLOR="Red"]508156[/COLOR]k total, 496760k used, 11396k free, 86464k buffers
Swap: [COLOR="Red"]262136[/COLOR]k total, 8268k used, 253868k free, 150836k cached
the Mem figure is the size of your RAM. The swap needs to but at least as big as the RAM for hibernate to work, because hibernate writes the RAM contents to swap to store it until wake-up.

Your indicated swap size is a smaller number than the RAM size. Why that is, I don't know, but that will stop hibernate from working, as far as I know.

I wanted to post a command to show the size of the partitions on you HD, but I can't find it. I'll get back to you.

---

### Post by audiomick on 2010-01-19
Can't find it..
I thought it should be
```
sudo fdisk -lu
```
but that is turning up block size for me, not bytes.

You could start gparted and have a look with that how big your swap really is. Is it possible that you got mixed up by an order of magnitude when you set it up?

---

### Post by eipapp on 2010-01-20
It returned the following:

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06370636

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   198691919    99345928+   7  HPFS/NTFS
/dev/sda2       198691920   240107489    20707785    f  W95 Ext'd (LBA)
/dev/sda5       198691983   203832719     2570368+  82  Linux swap / Solaris
/dev/sda6       203832783   240107489    18137353+  83  Linux

Maybe this will help ????

Regards,
Bruce

---

### Post by eipapp on 2010-01-20
Audomick - went into Gparted and got the following to see if this might help as well:

/dev/sda1  ntfs  /host  94.74Gib  Used 30.98Gib  Unused 63.76Gib  boot
/dev/sda2  extended    19.75Gib  Used  0            Unused 0             lba
/dev/sda5  linux-swap  2.45Gib    Used  0            Unused 0
/dev/sda6  ext2           17.3Gib    Used 322.07Mib  Unused 16.98Gib

Host or boot is where Win XP resides.

Bruce

---

