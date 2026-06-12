---
title: "Can't instal bootloader - Partition outside Disk"
date: 2012-05-13
forum: General Help
---

### Post by PremC on 2012-05-13
I am still puzzled as to what has changed in the Ubuntu OS between 10.10 and 11.04 (through 12.04)
10.10 installs flawlessly, bootloader and all. 
The newer ones install too, except for the bootloader which makes the system unusable.
If it worked before but no longer does, should this be reported as a bug?

Again, I have no disks, just the Revodrive.
This is my current disk configuration with Ubuntu 12.04 running just fine, after 10.10 install from a CD
and three upgrades over the net:


pc@pc-System:~$ sudo fdisk -lu
[sudo] password for pc: 
fdisk: unable to seek on /dev/sda: Invalid argument
pc@pc-System:~$ sudo parted -l
Error: Can't have a partition outside the disk!                           

Error: /dev/sdb: unrecognised disk label                                  

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/sil_bgacaidfeacd1: 47.9GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  47.9GB  47.9GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/sil_bgacaidfeacd5: 2094MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  2094MB  2094MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/sil_bgacaidfeacd2: 2094MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system     Flags
 1      1024B  2094MB  2094MB  primary  linux-swap(v1)


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/sil_bgacaidfeacd: 50.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      131kB   47.9GB  47.9GB  primary   ext4
 2      47.9GB  50.0GB  2094MB  extended
 5      47.9GB  50.0GB  2094MB  logical   linux-swap(v1)

---

### Post by oldfred on 2012-05-13
Moved to your own thread as your issue is a lot different than the thread you posted in.

From your post:

> Error: Can't have a partition outside the disk!                           

Error: /dev/sdb: unrecognised disk label                                  


From liveCD add these drivers as it looks like you are running RAID or LVM.

Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install gawk
sudo apt-get install xz-utils

I know this works on standard partitions but it may not work on your RAID. You probably should use RAID commands to fix. I do not know RAID.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by PremC on 2012-05-13
Ubuntu 10.10 CD installs flawlessly. None of the more recent CDs do.
I've tried them all, and I have also tried all of the alternate locations that the
installation process allowed me to select. None worked.

The OS changed the way it installs the bootloader in 11.04 and later.
Should this be reported as a bug?

---

### Post by PremC on 2012-05-13
Oh, and I forgot...
This is what my system looks like with Ubuntu 12.04 on it, and working

pc@pc-System:~$ sudo fdisk -lu
[sudo] password for pc: 
fdisk: unable to seek on /dev/sda: Invalid argument



pc@pc-System:~$ sudo parted -l
Error: Can't have a partition outside the disk!                           

Error: /dev/sdb: unrecognised disk label                                  

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/sil_bgacaidfeacd1: 47.9GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  47.9GB  47.9GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/sil_bgacaidfeacd5: 2094MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  2094MB  2094MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/sil_bgacaidfeacd2: 2094MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system     Flags
 1      1024B  2094MB  2094MB  primary  linux-swap(v1)


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/sil_bgacaidfeacd: 50.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      131kB   47.9GB  47.9GB  primary   ext4
 2      47.9GB  50.0GB  2094MB  extended
 5      47.9GB  50.0GB  2094MB  logical   linux-swap(v1)

---

### Post by PremC on 2012-05-15
oldfred,
 my system works perfectly. The listing I've posted is not the cause of the problem but rather
the end-result of it. Dartmaul, Shazzr, and I, were trying to do a clean install of the newer version of Ubuntu on an OCZ Revodrive which is a PCI-E card that installs as RAID-0 straight from the box.

It appears that both of them had given up. If they want to have 12.04 booting from their Revodrive, they will most likely have  to do what I have done.

Again, Ubuntu install worked perfectly in 10.10 and stopped working from  11.04 on.
Besides trying to help Dartmaul and Shazzr, I was hoping that someone familiar with
Ubuntu internals might read the post and connect the dots.

I can see now that I should have just reported this is a bug to the Ubuntu team and
stay out of this. Hijacking the thread was not my intention.
I apologize for my poor communication skills that caused all this.
Please consider this thread closed.

---

