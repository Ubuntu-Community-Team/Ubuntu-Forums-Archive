---
title: "Wubi boot menu gone missing"
date: 2010-05-01
forum: General Help
---

### Post by anlag on 2010-05-01
On a system with Windows 7, Ubuntu installed through Wubi. It was set up and working fine, until one day no boot menu of any kind shows up and it boots straight into Windows. I'm guessing some Windows update broke it.

Have searched around a bit for a fix, with many references to boot.ini but as this does not appear to exist in Windows 7 I'm not sure how to proceed. It's possible to go to Starup and Recovery settings though, where default boot OS is set, and it is possible to choose Ubuntu from there. Just a bit worried if we do this and reboot, there'll be no way back into Windows and if it doesn't work out right...

Did find a file called wubildr.mbr which seems mostly binary content, but some text lines as well at the end which suggest indeed some sort of boot error:

> Press space bar
Press   to start GRUB, any other key to boot previous MBR ...
Timeout :     
Invalid previous MBR. Press any key to start GRUB ...
Cannot find GRLDR.  to hold the screen, any other key to boot previous MBR ...
Error while reading MBR of  drive (hd0 ) 
Invalid boot indicator in partition table of 
Invalid sectors_per_track in partition table of 
Invalid start_sector in partition table of 
Invalid end_sector in partition table of 
No boot signature in partition table of 
Error: Cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart.
Try (hd0,0 ) :  EXT2:  NTFS4:  NTFS5:  NTFS5p:  FAT32:  FAT16:  FAT12:  non-MS: skip  Extended:  invalid or null  This partition is NTFS but with unknown boot record. Please
install Microsoft NTFS boot sectors to this partition correctly, or create an
FAT12/16/32 partition and place the same copy of GRLDR and MENU.LST there.                             hot-key        GRUª

Grateful for any advice. Should add here the reason I'm saying "we" is it's my girlfriend's machine and I don't have direct access to it so straightforward and ideally graphical solutions would be ideal.

Thanks.

---

### Post by garvinrick4 on 2010-05-01
Go to Windows command line and enter Code:

bcdedit


it should have a section with wublder or something close to that. That is where WUBI has attached itself to the Windows grub. If not there needs to be installed.


  	 	 	 	 	 	  Fix Wubi when will not boot  
 

      Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:  
 

 sudo mkdir /win  
 sudo mount /dev/sda1 /win  
 

 Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein  
 

 sudo mkdir /vdisk  
 sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk  
 

 Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.  
 

 To check the filesystem you can use:  
 

 sudo fsck /win/ubuntu/disks/root.disk

---

