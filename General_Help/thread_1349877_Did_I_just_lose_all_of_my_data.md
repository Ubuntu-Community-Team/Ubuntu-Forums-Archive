---
title: "Did I just lose all of my data?"
date: 2009-12-08
forum: General Help
---

### Post by ekological on 2009-12-08
Hey guys,
 
I built a NAS running Ubuntu with a 3ware 16-port controller:
 
[http://www.hardforums.com/showthread.php?t=1449908](http://www.hardforums.com/showthread.php?t=1449908)
 
I followed advice and created the filesystem with:
 
```
mkfs.xfs /dev/sdb
```
 
I have since migrated the 6TB RAID5 array (using four 2TB disks) to a 10TB RAID6 array and had no problems.
 
Today, I tried to move the OS drive to a USB key to further reduce power consumption. So I pulled the OS drive and installed the USB drive. I also created a bootable Ubuntu 9.10 USB key from which to install the OS. I was a bit scared to leave the 10TB storage array connected for fear of accidentally wiping out the data so I just pulled the PCIe card and installed the OS. When everything was up and running, I reinstalled the PCIe 3ware controller and fired up the NAS. I was busy getting the drivers and other software running and forgot how to set up samba, so I was unconcerned that the 10TB filesystem wasn't mounted. Since I installed the latest version of the 3ware drivers, I also saw that a new firmware was available, so I flashed the firmware of the 3ware card. Now I noticed that the 10TB /dev/sda (it was different with the USB drive installed and the original OS drive pulled) showed up as unallocated space.
 
What to do?? I'm in the process of running testdisk, but I wasn't sure what partition type to use.
 
TIA,
Chester

---

