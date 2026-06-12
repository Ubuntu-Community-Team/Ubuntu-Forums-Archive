---
title: "Swap problem"
date: 2011-06-12
forum: General Help
---

### Post by KRISHNASHK on 2011-06-12
i am running ubuntu 10.04 with 2gb swap allocated during installation. now i want to remove the swap partition without screwing up my grub. thanks

---

### Post by lmarmisa on 2011-06-12
Do you wish to run Ubuntu with no swap or maybe to shrink the current swap partition?.

---

### Post by wildmanne39 on 2011-06-12
> **KRISHNASHK said:**
> i am running ubuntu 10.04 with 2gb swap allocated during installation. now i want to remove the swap partition without screwing up my grub. thanksHi, swap is needed for sleep or hibernation. If you want to get rid of it you can use the livecd and use gparted then click swap off when you try to reclaim that empty space you need to watch what is teels you if the partition you reclaim it too,l is in the wrong place it will tell you that it will cause the system to be unbootable and you will have to reinstall grub, here is a guide to help.
[http://ubuntuguide.org/wiki/Manipulating_Partitions](http://ubuntuguide.org/wiki/Manipulating_Partitions)
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by KRISHNASHK on 2011-06-13
Can i use the disk utility to remove the swap partition. Will screw up my grub?

---

### Post by Elfy on 2011-06-13
If you remove the swap partition you need to comment it out in fstab.

Removing the partition won't affect grub - it might cause you boot issues if you've not dealt with fstab.

Put a # in front of the swap line is fstab, it'll look _something like_ 
```
UUID=1b0cdd7f-a563-44f8-b3b2-c303672d3d63 swap   swap    defaults        0 0
```

```
gksudo gedit /etc/fstab
```

Never used disk utility so can't comment on that.

---

### Post by KRISHNASHK on 2011-06-13
> **forestpiskie said:**
> If you remove the swap partition you need to comment it out in fstab.

Removing the partition won't affect grub - it might cause you boot issues if you've not dealt with fstab.

Put a # in front of the swap line is fstab, it'll look _something like_ 
```
UUID=1b0cdd7f-a563-44f8-b3b2-c303672d3d63 swap   swap    defaults        0 0
``````
gksudo gedit /etc/fstab
```Never used disk utility so can't comment on that.
by doing so the swap will nt be mounted right!

---

### Post by nzjethro on 2011-06-13
> **KRISHNASHK said:**
> by doing so the swap will nt be mounted right!

Yup, that's correct. You can create a swap file (not a separate partition) down the line if you decide you want to.

---

### Post by KRISHNASHK on 2011-06-15
> **nzjethro said:**
> Yup, that's correct. You can create a swap file (not a separate partition) down the line if you decide you want to.
thanks that worked. even upon not mounting the swap. my hard disk usage light always glows when i am on ubuntu.why? thanks

---

### Post by KRISHNASHK on 2011-06-15
> **forestpiskie said:**
> If you remove the swap partition you need to comment it out in fstab.

Removing the partition won't affect grub - it might cause you boot issues if you've not dealt with fstab.

Put a # in front of the swap line is fstab, it'll look _something like_ 
```
UUID=1b0cdd7f-a563-44f8-b3b2-c303672d3d63 swap   swap    defaults        0 0
``````
gksudo gedit /etc/fstab
```Never used disk utility so can't comment on that.
thanks that worked. even upon not mounting the swap. my hard disk usage light always glows when i am on ubuntu.why? thanks

---

### Post by Elfy on 2011-06-15
No idea - run top from a terminal and see what's going on.

---

### Post by KRISHNASHK on 2011-06-17
> **forestpiskie said:**
> No idea - run top from a terminal and see what's going on.
top - 14:52:22 up 7 min,  2 users,  load average: 0.01, 0.10, 0.08
Tasks: 149 total,   1 running, 148 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.0%us,  0.5%sy,  0.0%ni, 96.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    442556k total,   430572k used,    11984k free,    21860k buffers
Swap:  1945596k total,       76k used,  1945520k free,   136860k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1636 krishna   20   0  347m  95m  30m S    4 22.0   0:58.71 firefox-bin        
  998 root      20   0 55096  39m  12m S    2  9.2   0:14.58 Xorg               
 1727 krishna   20   0 87088  13m  10m S    1  3.1   0:01.54 gnome-terminal     
  196 root      20   0     0    0    0 S    0  0.0   0:00.06 scsi_eh_1          
 1431 krishna   20   0  9168 4068 2328 S    0  0.9   0:00.70 gconfd-2           
 1486 root      20   0  5620  732  456 S    0  0.2   0:00.08 udisks-daemon      
 1752 krishna   20   0  2620 1120  832 R    0  0.3   0:00.33 top                
    1 root      20   0  2872 1632 1140 S    0  0.4   0:00.56 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0        
    4 root      RT   0     0    0    0 S    0  0.0   0:00.58 migration/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:03.38 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.05 events/0           
   10 root      20   0     0    0    0 S    0  0.0   0:00.00 events/1           
this is wat i got! can u find y?

---

### Post by KRISHNASHK on 2011-06-17
> **forestpiskie said:**
> No idea - run top from a terminal and see what's going on.
top - 15:31:33 up 46 min,  2 users,  load average: 0.11, 0.11, 0.12
Tasks: 151 total,   1 running, 150 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us,  1.0%sy,  0.0%ni, 96.7%id,  1.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    442556k total,   434044k used,     8512k free,    25560k buffers
Swap:  1945596k total,    21924k used,  1923672k free,   126828k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1727 krishna   20   0 87212  12m 9828 S    2  3.0   0:03.50 gnome-terminal     
  998 root      20   0 56544  33m 6380 S    2  7.6   1:33.61 Xorg               
 1752 krishna   20   0  2620  988  700 R    1  0.2   0:08.06 top                
 1636 krishna   20   0  456m 102m  22m S    0 23.7   4:58.14 firefox-bin        
    1 root      20   0  2872 1312  984 S    0  0.3   0:00.57 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.05 ksoftirqd/0        
    4 root      RT   0     0    0    0 S    0  0.0   0:00.58 migration/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:03.38 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.04 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.33 events/0           
   10 root      20   0     0    0    0 S    0  0.0   0:00.05 events/1           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns              
this is what i got? can u figure out anythng! thanks

---

### Post by Elfy on 2011-06-17
Nothing untoward that I can see.

---

