---
title: "11GB of space used on a empty ex4 drive?"
date: 2011-03-02
forum: General Help
---

### Post by max1zzz on 2011-03-02
After a lot of work and some help from you guys here i got my powermac g3 up and running as a file server, i added a sata card and two 250GB hdd's which i promptley formatted as ex4, today i noticed one of the drives (the empty one) shows as having 11gb used, at first i thought it was a artifact of samba, but i cheacked the atual comp and ubuntu shows the drive as having 11GB used  but it is compleatley empty? i then cheacked the outher drive which about 30GB of data on it, but it shows as having 40GB used?

any help would be appreciated
Thanks 
Max1zzz

---

### Post by jerome1232 on 2011-03-02
Trash?

What does du show? Use sudo in case there are files only readable by root on there.

```
sudo du -hx /path/to/filesystem/here
```

---

### Post by Smart Viking on 2011-03-02
This may be caused by 5% of the file system being reserved for root.

Run
```
tune2fs -l /dev/partition-name
```as root and paste the output here.

You could try to change it with
```
tune2fs -r number-of-blocks /dev/partition-name

```but be sure to unmount it first in case.

---

### Post by max1zzz on 2011-03-02
jerome1232: the 2 drive output this:
```
max@max-desktop-server:~$ sudo du -hx /media/Archive_Disk_1
[sudo] password for max: 
16K    /media/Archive_Disk_1/lost+found
501M    /media/Archive_Disk_1/Cd + Dvd's/Playstation Games/PS2/Crash_Bandicoot_The_Wrath_Of_Cortex_[Platinum]
4.2G    /media/Archive_Disk_1/Cd + Dvd's/Playstation Games/PS2/Grand_Theft_Auto_San_Andreas
4.4G    /media/Archive_Disk_1/Cd + Dvd's/Playstation Games/PS2/LEGO_Star_wars_2
610M    /media/Archive_Disk_1/Cd + Dvd's/Playstation Games/PS2/Lego_Star_Wars_[Platinum]
431M    /media/Archive_Disk_1/Cd + Dvd's/Playstation Games/PS2/Robot_Wars_Arenas_of_Destruction
4.3G    /media/Archive_Disk_1/Cd + Dvd's/Playstation Games/PS2/Call_of_Duty_Finest_Hour
15G    /media/Archive_Disk_1/Cd + Dvd's/Playstation Games/PS2
15G    /media/Archive_Disk_1/Cd + Dvd's/Playstation Games
592M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Windows (OS's)/xp_pro_sp2_[vlk]_[Non_legit]
566M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Windows (OS's)/xp_home_sp3
474M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Windows (OS's)/xp home retail
600M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Windows (OS's)/win95_[OSR2_OEM_with_USB_Support]
2.2G    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Windows (OS's)
558M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Apps + Drivers/Drivers/Sapphire_Install_Driver_CD_12-107_[8.560]_ATI_Catalyst_Driver_Suite_9.4
362M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Apps + Drivers/Drivers/Start_up_driver_computer_video_and_audio_product
255M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Apps + Drivers/Drivers/Kworld_Plus_TV_Drivers_manual_Utilities_[DVD_Maker_USB_2.0]
279M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Apps + Drivers/Drivers/Soundblaster_PCI64V
1.5G    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Apps + Drivers/Drivers
429M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Apps + Drivers/Programs/Bvrp_Classic_Phone_Tools_4.01
20M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Apps + Drivers/Programs/CyberLink_PowerDVD_XP_4.0
449M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Apps + Drivers/Programs
1.9G    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Apps + Drivers
643M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Service_Packs/nt4 sp4 install
643M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Service_Packs
269M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Games/Age_of_Empires_Gold
646M    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Games/Unreal_Gold
5.6G    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Games/NecroVisioN
6.5G    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff/Games
12G    /media/Archive_Disk_1/Cd + Dvd's/Windows stuff
690M    /media/Archive_Disk_1/Cd + Dvd's/Linux/OS'S/Ubuntu/i386 Intel + AMD 32bit [x86]/ubuntu-9.10-alternate-i386
690M    /media/Archive_Disk_1/Cd + Dvd's/Linux/OS'S/Ubuntu/i386 Intel + AMD 32bit [x86]
681M    /media/Archive_Disk_1/Cd + Dvd's/Linux/OS'S/Ubuntu/PPC (MAC)/ubuntu-8.04.1-desktop-powerpc
710M    /media/Archive_Disk_1/Cd + Dvd's/Linux/OS'S/Ubuntu/PPC (MAC)/ubuntu-10.10-desktop-powerpc
685M    /media/Archive_Disk_1/Cd + Dvd's/Linux/OS'S/Ubuntu/PPC (MAC)/ubuntu-10.10-alternate-powerpc
695M    /media/Archive_Disk_1/Cd + Dvd's/Linux/OS'S/Ubuntu/PPC (MAC)/ubuntu-10.04-desktop-powerpc
706M    /media/Archive_Disk_1/Cd + Dvd's/Linux/OS'S/Ubuntu/PPC (MAC)/ubuntu-9.10-desktop-powerpc
3.4G    /media/Archive_Disk_1/Cd + Dvd's/Linux/OS'S/Ubuntu/PPC (MAC)
4.1G    /media/Archive_Disk_1/Cd + Dvd's/Linux/OS'S/Ubuntu
4.1G    /media/Archive_Disk_1/Cd + Dvd's/Linux/OS'S
4.1G    /media/Archive_Disk_1/Cd + Dvd's/Linux
301M    /media/Archive_Disk_1/Cd + Dvd's/Mac stuff/Drivers/AirPort_3.2
301M    /media/Archive_Disk_1/Cd + Dvd's/Mac stuff/Drivers
650M    /media/Archive_Disk_1/Cd + Dvd's/Mac stuff/MacFormat_Disks/ISIM_Master_Clips_5000_[MF83b_NOV_99]
650M    /media/Archive_Disk_1/Cd + Dvd's/Mac stuff/MacFormat_Disks
950M    /media/Archive_Disk_1/Cd + Dvd's/Mac stuff
31G    /media/Archive_Disk_1/Cd + Dvd's
31G    /media/Archive_Disk_1
max@max-desktop-server:~$ 

``` and
```
max@max-desktop-server:~$ sudo du -hx /media/Archive_Disk_2
16K    /media/Archive_Disk_2/lost+found
28K    /media/Archive_Disk_2
max@max-desktop-server:~$ 

```
Smart Viking: dosen't seem to be able to find the hdd?
```
x@max-desktop-server:~$ tune2fs -l /dev/Archive_Disk_1
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: No such file or directory while trying to open /dev/Archive_Disk_1
Couldn't find valid filesystem superblock.
max@max-desktop-server:~$ tune2fs -l /dev/sda
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Permission denied while trying to open /dev/sda
Couldn't find valid filesystem superblock.
max@max-desktop-server:~$ sudo tune2fs -l /dev/sda
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Bad magic number in super-block while trying to open /dev/sda
Couldn't find valid filesystem superblock.
max@max-desktop-server:~$ sudo tune2fs -l /dev/sdb
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Bad magic number in super-block while trying to open /dev/sdb
Couldn't find valid filesystem superblock.
max@max-desktop-server:~$ 

```

---

### Post by jerome1232 on 2011-03-02
So disk 1 does indeed have about 31 GB's of stuff on it.

Disk 2 however has nothing on it and you said it claims 11 GB's are used?

Probably is the 5% reserved, easy enough to switch off if desired.

As for tune2fs you need the device path not the mount point.

You can get the device path from the mount command like this, then rerun those tune2fs commands.

```
mount | grep Archive
```

---

### Post by max1zzz on 2011-03-02
> **jerome1232 said:**
> So disk 1 does indeed have about 31 GB's of stuff on it.

Disk 2 however has nothing on it and you said it claims 11 GB's are used?

Probably is the 5% reserved, easy enough to switch off if desired.

As for tune2fs you need the device path not the mount point.

You can get the device path from the mount command like this, then rerun those tune2fs commands.

```
mount | grep Archive
```
so how do you turn it off?

---

### Post by Smart Viking on 2011-03-02
> **max1zzz said:**
> Smart Viking: dosen't seem to be able to find the hdd?


Use the name of the partition and not the name of the device, so partition one on /dev/sdb would be /dev/sdb1

---

### Post by max1zzz on 2011-03-02
> **Smart Viking said:**
> Use the name of the partition and not the name of the device, so partition one on /dev/sdb would be /dev/sdb1
ok... will try after school tomorrow, leaving some transfers going overnight so can't fiddle with the drive atm

---

### Post by psusi on 2011-03-02
Check the output of df -h.  It should be correct.  There is a known bug in gnome if you use the gui to look at the space of a drive where it computes used = total - available instead of reporting the actual used space.  It is not all available because by default, the kernel keeps a 5% emergency reserve.

---

