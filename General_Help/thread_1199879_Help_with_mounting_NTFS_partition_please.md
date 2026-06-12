---
title: "Help with mounting NTFS partition please"
date: 2009-06-29
forum: General Help
---

### Post by ryy705 on 2009-06-29
Hello,

I've tried to mount my Windows Vista partition by following the direction on [kubuntuguide.org]("http://kubuntuguide.org/Jaunty#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29").  It asks to install ntfs-3g,  add user to a group called fuse(I added both my regular account and root to fuse), and enter the following line to /etc/fstab:

/dev/sda2 /mnt/WindowsNTFS ntfs-3g quiet,defaults,rw 0 0

I did all this. The WinVista directory now shows up under /media but there's nothing inside it.

This what my /etc/fstab file currently looks like:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4cf17e41-44c3-407d-a347-8342cc8132e3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e83dc45d-24de-45a9-b647-72cf7f81d67c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
# mine
#/dev/sda2 /media/windows ntfs-fuse auto,gid=1001,umask=0002 0 0
/dev/sda2 /mnt/WindowsNTFS ntfs-3g quiet,defaults,rw 0 0

```

And this is what I get from sudo fdisk -l
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        8586    68915039+   7  HPFS/NTFS
/dev/sda3            8587       14341    46227037+  83  Linux
/dev/sda4           14342       14593     2024190    5  Extended
/dev/sda5           14342       14593     2024158+  82  Linux swap / Solaris

```

Could someone kindly tell me what I'm doing wrong.

---

### Post by Polaris96 on 2009-06-29
Try this:

sudo mkdir Winpart
sudo mount -t ntfs /dev/sda2 Winpart

and tell me what it says, please.
if you don't get an error message, your Vista partition will mounted in the Winpart directory.

Then we can check deeper into fstab.  It should work, but I'll admit I've never worked with vista.

---

### Post by pastalavista on 2009-06-29
If Vista wasn't properly shut down or had updates or configs to finish on restart, it won't be mountable under Linux. Boot into Windows, make sure all processes are shut down amd all updates, virus scans, etc are completed. Then reboot and try Ubuntu again.

---

### Post by ryy705 on 2009-06-30
Hello,

Thank you for the prompt responses.

I could not believe how easy it was to do.
I updated Win Vista all day long and did the following:

sudo mkdir Winpart
sudo mount -t ntfs /dev/sda2 Winpart

It worked great last night.

However,  I cannot access this morning.  ls Winpart echoes nothing.:sad:
Windows does not need any more updates, I just checked. Any suggestions guys?  Many thanks in advance fellas.

---

### Post by Cuba71 on 2009-06-30
You may have to mount de partition every time you reboot

---

### Post by Bucky Ball on 2009-06-30
From Synaptic Package Manager install 

ntfs-3g

You will find it as 'NTFS Disk Manager' or something like that in your drop down menus. Open the app and it will ask you which NTFS partitions you would like to use. It automatically creates the entries in the fstab for you. When this is done, check the fstab file as you might need to remove the one you have entered manually.

---

### Post by ryy705 on 2009-06-30
hmm..
It seems that I do have to mount it every time.  Which is exceptable to me.
I'll make an alias and keep things simple. I'll try this for couple of days.
Thanks guys.

---

### Post by Bucky Ball on 2009-06-30
Yea, I've found the actual Vista partition to have some peculiarites with security and locking the partition and stuff. I only keep Windows programs and the Vista install on it anyway so I have no reason to access the thing from Ubuntu anyways.

---

