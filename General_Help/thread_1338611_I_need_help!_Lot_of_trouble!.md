---
title: "I need help! Lot of trouble!"
date: 2009-11-26
forum: General Help
---

### Post by Runtest on 2009-11-26
A good while back, a long time ago, when I was starting in my IT career professionally, I setup a Windows 2003 server. It has raid 5 I believe on 4 hard drives. I was stupid and did not setup a backup. 

I received a call from the CPA that I set the server up for recently. She requested that I install a cheap simple backup. I suggested a tape drive setup, she digressed she wanted something cheaper. So I setup a removable HDD.

I was in the middle of setting up the backup when the computer froze. It forced me to cold reboot. When it came back on, it intermediately froze. I noticed a message at the bottom right hand corner of the screen saying it was repairing the array. It froze for 4 hours. I turned it off again.

When it came back this time, it says. Windows can not start, can not find. /Windows/SYSTEM32/CONFIG

Now I knew I was in trouble. So, I NEED THAT DATA. I popped out my Ubuntu CD and went live. It is the latest release. I tried everything. mdadm mount ect. I just do not know enough to mount the raid. It sees there is a raid. It is in the list. I just do not know what to do from there. She has payroll due Friday, and while I have learned my lesson I need some serious help. I would be more than happy to pay for help. If someone can help me get it working. I would be happy to make a donation.

If anyone could lend me a hand it would be greatly appreciated. I have an external hdd mounted for read/write. If I can get the raid data copied to this I can send the server off for reapir and reload. I would do it myself but I want the manufacturer to check the hardware and I may say screw windows and throw Linux on there.

If anyone could help I would be very happy. Also my MSN is <snip>. Thank you for ANY help you can provide.

I was thinking that ubuntu usually automatically mounted isw Intel hardware raids. So if it is damaged I need to know how to repair it enough to copy and paste the info.

---

### Post by Runtest on 2009-11-26
```
ubuntu@ubuntu:~$ root
The program 'root' is currently not installed.  You can install it by typing:
sudo apt-get install root-system-bin
You will have to enable the component called 'universe'
root: command not found
ubuntu@ubuntu:~$ sudo -h
usage: sudo [-n] -h | -K | -k | -L | -V | -v
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
ubuntu@ubuntu:~$ sudo 
usage: sudo [-n] -h | -K | -k | -L | -V | -v
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
ubuntu@ubuntu:~$ sudo -n
usage: sudo [-n] -h | -K | -k | -L | -V | -v
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
ubuntu@ubuntu:~$ sudo -e
usage: sudo [-n] -h | -K | -k | -L | -V | -v
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
ubuntu@ubuntu:~$ cleqar
No command 'cleqar' found, did you mean:
 Command 'clear' from package 'ncurses-bin' (main)
cleqar: command not found
ubuntu@ubuntu:~$ clear

ubuntu@ubuntu:~$ mdadm
Usage: mdadm --help
  for help
ubuntu@ubuntu:~$ mdadm -h
mdadm is used for building, managing, and monitoring
Linux md devices (aka RAID arrays)
Usage: mdadm --create device options...
            Create a new array from unused devices.
       mdadm --assemble device options...
            Assemble a previously created array.
       mdadm --build device options...
            Create or assemble an array without metadata.
       mdadm --manage device options...
            make changes to an existing array.
       mdadm --misc options... devices
            report on or modify various md related devices.
       mdadm --grow options device
            resize/reshape an active array
       mdadm --incremental device
            add a device to an array as appropriate
       mdadm --monitor options...
            Monitor one or more array for significant changes.
       mdadm device options...
            Shorthand for --manage.
Any parameter that does not start with '-' is treated as a device name
or, for --examine-bitmap, a file name.
The first such name is often the name of an md device.  Subsequent
names are often names of component devices.

 For detailed help on the above major modes use --help after the mode
 e.g.
         mdadm --assemble --help
 For general help on options use
         mdadm --help-options
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb52cb52

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121600   976751968+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb52cb52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121600   976751968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000006c

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000006c

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70796f19

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001    b  W95 FAT32
ubuntu@ubuntu:~$ clear 

ubuntu@ubuntu:~$ dmraid
ERROR: no arguments/options given (-h for help)

ubuntu@ubuntu:~$ dmraid -h
dmraid: Device-Mapper Software RAID tool

* = [-d|--debug]... [-v|--verbose]... [-i|--ignorelocking]

dmraid    {-a|--activate} {y|n|yes|no} *
    [-f|--format FORMAT[,FORMAT...]]
    [-P|--partchar CHAR]
    [-p|--no_partitions]
    [--separator SEPARATOR]
    [-t|--test]
    [-Z|--rm_partitions] [RAID-set...]

dmraid    {-b|--block_devices} *
    [-c|--display_columns][FIELD[,FIELD...]]...
    [device-path...]

dmraid    {-h|--help}

dmraid    {-l|--list_formats} *

dmraid    {-n|--native_log} *
    [-f|--format FORMAT[,FORMAT...]]
    [--separator SEPARATOR]
    [device-path...]

dmraid    {-r|--raid_devices} *
    [-c|--display_columns][FIELD[,FIELD...]]...
    [-D|--dump_metadata]
    [-f|--format FORMAT[,FORMAT...]]
    [--separator SEPARATOR]
    [device-path...]

dmraid    {-r|--raid_devices} *
    {-E|--erase_metadata}
    [-f|--format FORMAT[,FORMAT...]]
    [--separator SEPARATOR]
    [device-path...]

dmraid    {-s|--sets}...[a|i|active|inactive] *
    [-c|--display_columns][FIELD[,FIELD...]]...
    [-f|--format FORMAT[,FORMAT...]]
    [-g|--display_group]
    [--separator SEPARATOR]
    [RAID-set...]

dmraid    {-f|--format FORMAT}
     {-C|--create RAID-set} 
    {--type RAID-level}
    [--size [0-9]...[kKgG][bB]]
    [--str[i[de]] [0-9]...[kK][bB]]
    {--disk[s] "device-path[, device-path..."}

dmraid    {-x|--remove RAID-set} 

dmraid    {-R|--rebuild} RAID-set [drive_name]

dmraid    [{-f|--format FORMAT}]
    {-S|--spare [RAID-set]} 
    {-M|--media "device-path"}

dmraid    {-V/--version}

ubuntu@ubuntu:~$ clear

ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sdd: isw, "isw_ecejacjdba", GROUP, ok, 976773166 sectors, data@ 0
/dev/sdc: isw, "isw_ecejacjdba", GROUP, ok, 976773166 sectors, data@ 0
/dev/sdb: isw, "isw_ecejacjdba", GROUP, ok, 976773166 sectors, data@ 0
/dev/sda: isw, "isw_ecejacjdba", GROUP, ok, 976773166 sectors, data@ 0
ubuntu@ubuntu:~$ dmraid -h
dmraid: Device-Mapper Software RAID tool

* = [-d|--debug]... [-v|--verbose]... [-i|--ignorelocking]

dmraid    {-a|--activate} {y|n|yes|no} *
    [-f|--format FORMAT[,FORMAT...]]
    [-P|--partchar CHAR]
    [-p|--no_partitions]
    [--separator SEPARATOR]
    [-t|--test]
    [-Z|--rm_partitions] [RAID-set...]

dmraid    {-b|--block_devices} *
    [-c|--display_columns][FIELD[,FIELD...]]...
    [device-path...]

dmraid    {-h|--help}

dmraid    {-l|--list_formats} *

dmraid    {-n|--native_log} *
    [-f|--format FORMAT[,FORMAT...]]
    [--separator SEPARATOR]
    [device-path...]

dmraid    {-r|--raid_devices} *
    [-c|--display_columns][FIELD[,FIELD...]]...
    [-D|--dump_metadata]
    [-f|--format FORMAT[,FORMAT...]]
    [--separator SEPARATOR]
    [device-path...]

dmraid    {-r|--raid_devices} *
    {-E|--erase_metadata}
    [-f|--format FORMAT[,FORMAT...]]
    [--separator SEPARATOR]
    [device-path...]

dmraid    {-s|--sets}...[a|i|active|inactive] *
    [-c|--display_columns][FIELD[,FIELD...]]...
    [-f|--format FORMAT[,FORMAT...]]
    [-g|--display_group]
    [--separator SEPARATOR]
    [RAID-set...]

dmraid    {-f|--format FORMAT}
     {-C|--create RAID-set} 
    {--type RAID-level}
    [--size [0-9]...[kKgG][bB]]
    [--str[i[de]] [0-9]...[kK][bB]]
    {--disk[s] "device-path[, device-path..."}

dmraid    {-x|--remove RAID-set} 

dmraid    {-R|--rebuild} RAID-set [drive_name]

dmraid    [{-f|--format FORMAT}]
    {-S|--spare [RAID-set]} 
    {-M|--media "device-path"}

dmraid    {-V/--version}

ubuntu@ubuntu:~$ sudo dmraid -ay -fisw
RAID set "isw_ecejacjdba_RAID 10-0" was activated
RAID set "isw_ecejacjdba_RAID 10-1" was activated
RAID set "isw_ecejacjdba_RAID 10" was not activated
ubuntu@ubuntu:~$ sudo mkdir /media/raid_disk
ubuntu@ubuntu:~$ sudo mount /dev/mapper/"isw_evejacjdba_RAID 10-0" /media/raid_disk
mount: special device /dev/mapper/isw_evejacjdba_RAID 10-0 does not exist
ubuntu@ubuntu:~$ sudo mount /dev/mapper/"isw_evejacjdba_RAID%2010-0" /media/raid_disk
mount: special device /dev/mapper/isw_evejacjdba_RAID%2010-0 does not exist
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_evejacjdba_RAID%2010-0 /media/raid_disk
mount: special device /dev/mapper/isw_evejacjdba_RAID%2010-0 does not exist
ubuntu@ubuntu:~$ sudo mount /dev/mapper/"isw_ecejacjdba_RAID 10-1" /media/raid_disk
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ 

```That is what I have hit. Any help is really needed. Thank you.

```
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/mapper/"isw_ecejacjdba_RAID 10-0" /media/raid_disk
NTFS signature is missing.
Failed to mount '/dev/mapper/isw_ecejacjdba_RAID 10-0': Invalid argument
The device '/dev/mapper/isw_ecejacjdba_RAID 10-0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
ubuntu@ubuntu:~$ sudo mount -t hpfs /dev/mapper/"isw_ecejacjdba_RAID 10-0" /media/raid_disk
mount: wrong fs type, bad option, bad superblock on /dev/mapper/isw_ecejacjdba_RAID 10-0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ 

```

---

### Post by Runtest on 2009-11-26
I also tried this.

```
ubuntu@ubuntu:~$ sudo mount -t hpfs /dev/mapper/"isw_ecejacjdba_RAID 10" /media/raid_disk
mount: special device /dev/mapper/isw_ecejacjdba_RAID 10 does not exist
ubuntu@ubuntu:~$ dmraid -ay
ERROR: you must be root
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_ecejacjdba_RAID 10-0" already active
RAID set "isw_ecejacjdba_RAID 10-1" already active
RAID set "isw_ecejacjdba_RAID 10" was not activated
ubuntu@ubuntu:~$ sudo dmraid -ay -f ntfs
ERROR: invalid format for -f at (see -l)
ubuntu@ubuntu:~$ dmraid -l
asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1,01)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs
ubuntu@ubuntu:~$ dmraid -ay -f isw
ERROR: you must be root
ubuntu@ubuntu:~$ sudo dmraid -ay -f isw
RAID set "isw_ecejacjdba_RAID 10-0" already active
RAID set "isw_ecejacjdba_RAID 10-1" already active
RAID set "isw_ecejacjdba_RAID 10" was not activated
ubuntu@ubuntu:~$ man mount
ubuntu@ubuntu:~$ clear

ubuntu@ubuntu:~$ ntfs-3g
ntfs-3g: No device is specified.

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2009 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  http://ntfs-3g.org
ubuntu@ubuntu:~$ dmraid -ay
ERROR: you must be root
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_ecejacjdba_RAID 10-0" already active
RAID set "isw_ecejacjdba_RAID 10-1" already active
RAID set "isw_ecejacjdba_RAID 10" was not activated
ubuntu@ubuntu:~$ ntfs-3g /dev/mapper/"isw_ecejacjdba_RAID 10-0" /media/raid_diskUnprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged
ubuntu@ubuntu:~$ sudo ntfs-3g /dev/mapper/"isw_ecejacjdba_RAID 10-0" /media/raid_disk
NTFS signature is missing.
Failed to mount '/dev/mapper/isw_ecejacjdba_RAID 10-0': Invalid argument
The device '/dev/mapper/isw_ecejacjdba_RAID 10-0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
ubuntu@ubuntu:~$ 

```

---

### Post by mechro on 2009-11-26
I don't know much about RAID but couldn't you try one drive at a time? Either unplug the other three, or take out a drive and try it in another computer.

Probably a stupid idea but you sound desperate.

---

### Post by Runtest on 2009-11-26
Thanks for the reply. But I think if you take one of the HDDS out and plug it in somewhere else it might break the array and really mess things up. I am not 100% on that.

---

### Post by Talon2 on 2009-11-26
I'd throw you a bone if I had one.  The problem is that I'm a Unix/Linux/Other geek.  I suspect a lot of others here may be similar.

Have you thought about finding a windows forum?

---

### Post by cariboo on 2009-11-26
We aren't really here to help with Windows problems, but try this:

```
Insert the Windows XP install CD into CD-ROM drive, and then restart the computer. 
Click to select any options that are required to start the computer
When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
If you have a dual-boot or multiple-boot computer, select the installation that you want 
to access from the Recovery Console. When you are prompted to do so, 
type the Administrator password. If the administrator password is blank, just press ENTER.
At the Recovery Console command prompt, type the  following lines, pressing ENTER 
after you type each line:

md tmp
copy c:\windows\system32\config\system c:\windows\tmp\system.bak
copy c:\windows\system32\config\software c:\windows\tmp\software.bak
copy c:\windows\system32\config\sam c:\windows\tmp\sam.bak
copy c:\windows\system32\config\security c:\windows\tmp\security.bak
copy c:\windows\system32\config\default c:\windows\tmp\default.bak

delete c:\windows\system32\config\system
delete c:\windows\system32\config\software
delete c:\windows\system32\config\sam
delete c:\windows\system32\config\security
delete c:\windows\system32\config\default

copy c:\windows\repair\system c:\windows\system32\config\system
copy c:\windows\repair\software c:\windows\system32\config\software
copy c:\windows\repair\sam c:\windows\system32\config\sam
copy c:\windows\repair\security c:\windows\system32\config\security
copy c:\windows\repair\default c:\windows\system32\config\default

Type exit to quit Recovery Console. Your computer will restart
```

---

### Post by Runtest on 2009-11-26
Its a windows 2003 server. When I tried to stick in a boot disk it blue screens.

---

### Post by NoaHall on 2009-11-26
Hm. Does it have another drive with the OS on(not the RAID)?

---

### Post by WildeBeest on 2009-11-26
Take a look at diskinternals. They have a Raid recovery utility.

[http://www.diskinternals.com/](http://www.diskinternals.com/)

---

### Post by Runtest on 2009-11-27
The issues I am running in to seem to be based on hardware failure on the raid controllers part. So it ruined the raid setup. I am going to order in like 5 different sata to usb adapters and try this raid recovery on a different machine.

---

### Post by Runtest on 2009-11-27
I am going to try this and report back.


**DiskInternals [Raid Recovery]("http://www.diskinternals.com/raid-recovery/")**

---

### Post by jacobs444 on 2009-11-27
Good Luck, sounds like you had to learn the hardest way possible.

---

