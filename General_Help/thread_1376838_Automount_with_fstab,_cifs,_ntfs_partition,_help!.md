---
title: "Automount with fstab, cifs, ntfs partition, help!"
date: 2010-01-09
forum: General Help
---

### Post by djstatusent on 2010-01-09
I have not been able to automount my Windows ntfs partition(sda2) via Ubuntu using fstab, I am always getting automount errors after modifying its properties.  I believe it has something to do with user, guest or UID.  I just have been unable to find my answer...excuse my n00bnesss, early thanks community!!  This is my first post!

here's what my SMBTREE and FSTAB look like..
SMBTREE
```

elij@elij-laptop:~$ smbtree
Enter elij's password: 
WORKGROUP
	\\ELIJ-LAPTOP    		
		\\ELIJ-LAPTOP\video2         	
		\\ELIJ-LAPTOP\IPC$           	IPC Service (elij-laptop server (Samba, Ubuntu))
		\\ELIJ-LAPTOP\print$         	Printer Drivers
elij@elij-laptop:~$

```
FSTAB
```

  GNU nano 2.0.9              File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0b2e8d21-ae70-dea9-6492-e92f0ab8e293 /               ext3    relatime,erro$
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//elij-laptop    /media        cifs    user,iocharset=utf8 0 0
/dev/sda2       /media/music     ntfs   guest,auto,exec,utf8 0 0

```

---

### Post by b0b138 on 2010-01-09
post output of ```
sudo fdisk -l
```

---

### Post by djstatusent on 2010-01-09
thanks for the quick reply...

```

elij@elij-laptop:~$ sudo fdisk -l
[sudo] password for elij: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4231171e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         830     6665216   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             830       16340   124584798    7  HPFS/NTFS
/dev/sda3   *       16341       18168    14683410   af  HFS / HFS+
/dev/sda4           18169       19457    10353892+  83  Linux
elij@elij-laptop:~$

```

---

### Post by b0b138 on 2010-01-09
Try this line...

```
/dev/sda2    /media/music    ntfs    defaults,umask=007,gid=46,noatime   0       0
```


and remove //elij-laptop    /media        cifs    user,iocharset=utf8 0 0

---

### Post by djstatusent on 2010-01-09
i need
```

//elij-laptop /media cifs user,iocharset=utf8 0 0

```
...to stay, I use that mount for XBMC.  Should I still use the line that you posted?

---

### Post by Jackzor on 2010-01-09
What about using:

sudo apt-get install ntfs-config

Just set that up thats what I used. Its simple.

---

### Post by ThaddeusW on 2010-01-09
Are you trying to mount the disk at boot time or by hand? Ubuntu should let you do this via pmount which enables users to mount the disk and read/write to it without needing root permission. Gnome uses pmount to auto mount disks when they are detected by the USB system. I have not used XFCE is a long time but it too should work the same way. 

For NTFS use the NTFS-3G driver. It uses FUSE which stands for File System in User Space. I have successfully used it to safely read and write to a USB HDD formatted NTFS.

ntfs-3g should be installed by default, if not for some reason install it by typing the following in the console:
```
sudo apt-get install ntfs-3g
```

Then change the file system type in your fstab to ntfs-3g. The NTFS line should look like this:
```
/dev/sda1 /xxxxxx/music ntfs-3g defaults,noatime,locale=en_US.UTF-8 0 0
```
See if this works.

As for CIFS automounting this is a string I pull up when searching via google:
```
//192.168.1.1/Shared /mnt/shared cifs auto,user,username=xxxxx,workgroup=xxxxx,password=xxxxx,uid=500,gid=500,file_mode=0777,dir_mode=0777,rw 0 0
```

Its a long string but this should allow you to mount the share with full read/write permissions. cifs is used here as smbfs is outdated. You should be able to pull up tons of stuff by searching for "cifs fstab" on Google (without the quotes of course). Same goes for "ntfs-3g fstab".

---

### Post by djstatusent on 2010-01-09
b0b138, the code you gave me returned with:

"Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda2 on /media/music"


Jackzor and ThaddeusW, will that affect my ability to boot into that partition at a later date before I make those commands??  I don't know much about ntfs vs ntfs-3g, but I do run a triple boot on this machine, it would be a shame to have corruption.

---

### Post by Jackzor on 2010-01-09
> **djstatusent said:**
> b0b138, the code you gave me returned with:

"Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda2 on /media/music"


Jackzor and ThaddeusW, will that affect my ability to boot into that partition at a later date before I make those commands??  I don't know much about ntfs vs ntfs-3g, but I do run a triple boot on this machine, it would be a shame to have corruption.


ntfs-config will not effect the partition except for mounting it when you boot to ubuntu.

Everything will be fine.

Unless some freak thing happens. I have used it twice now and it works just fine.

---

### Post by Jackzor on 2010-01-09
Run sudo apt-get install ntfs-config

After it installs head to the System->Administration menu and pick the NTFS Configuration Tool.

Check the box for "Add," click in the "Mount point" column to give it a name (Storage, perhaps?), and hit "Apply." Check both boxes on the next window to allow read/write access, and hit OK, and you're done. Now the drive with all your stuff is accessible to Windows and Linux at all times.

---

