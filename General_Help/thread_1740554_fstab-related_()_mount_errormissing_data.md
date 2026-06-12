---
title: "fstab-related (?) mount error/missing data"
date: 2011-04-27
forum: General Help
---

### Post by Feilin on 2011-04-27
I used the ntfs-config utility to mount my windows drives automatically at startup. While doing so, I had my USB-HDD still attached, and after making changes and rebooting, it did something unknown I didn't expect and I cannot mount my USB-HDD again, and it gives me the following error message:


     Error mounting: mount exited with exit code 1: helper failed with:
     mount: only root can mount /dev/sdb1 on /media/MyUSBDrive

I did manage to open it somehow, but then all the data was erased apart from ~3 GiB [edit: it's got some kind of extra drive built-in which is mounted as a CD-ROM drive, and when I open that one first all the files are missing in the actual drive, otherwise I get the message above]. I don't know what information I should include here, but my fstab looks like this:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sda6 :
UUID=e09c83ab-dc5b-485f-a21b-57e1ecba5265    /    ext3    relatime,errors=remount-ro    0    1
#Entry for /dev/sda7 :
UUID=fc8ca6c7-d5be-46f4-93a6-0a3e2631961c    /home    ext3    relatime    0    2
#Entry for /dev/sda1 :
UUID=6468751C6874EDE4    /media/6468751C6874EDE4    ntfs-3g    defaults,nosuid,nodev,locale=C    0    0
#Entry for /dev/sda2 :
UUID=1C1F3EFD4F6904C1    /media/Files    ntfs-3g    defaults,nosuid,nodev,locale=C    0    0
#Entry for /dev/sdb1 :
UUID=5ECF89B252B372CF    /media/MyUSBDrive    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
#Entry for /dev/sda5 :
UUID=4c223586-8f82-4219-bcef-7366fc64de6a    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8    0    0


Here is my "sudo fdisk -lu" results:


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x37cf331c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/sda2        40965750   245762369   102398310    7  HPFS/NTFS
/dev/sda3       245762370   625137344   189687487+   5  Extended
/dev/sda5       609506100   625137344     7815622+  82  Linux swap / Solaris
/dev/sda6       245762496   265297409     9767457   83  Linux
/dev/sda7       265297473   609490034   172096281   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders, total 975400960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d14aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   975386474   487693206    7  HPFS/NTFS



This line in terminal:
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1

Gives:
fuse: failed to access mountpoint /media/sdb1: No such file or directory


What should I do to recover my files and fix the mount error? [edit: at the very least, how do I backup my files onto my internal HDD so I can format it and recover it in this manner]

---

### Post by Feilin on 2011-04-27
Would it be access it with a live CD, or is some mounting related information written to the drive itself that prevents any mounting?

I'm also just assuming that my dual-boot windows 7 isn't going to help me either...

---

### Post by ~Plue on 2011-04-27
> **Feilin said:**
> 
     Error mounting: mount exited with exit code 1: helper failed with:
     mount: only root can mount /dev/sdb1 on /media/MyUSBDrive
```

# /etc/fstab: static file system information.
.
#Entry for /dev/sdb1 :[COLOR=Magenta]
UUID=5ECF89B252B372CF    /media/MyUSBDrive    ntfs defaults,nls=utf8,umask=0222,nosuid,nodev    0    0[/COLOR]
.

```
The highlighted portion is whats causing trouble... using 'defaults' would imply the nouser option which means only root could mount the partition at either the boot time or when you use sudo mount /device/name etc...  you could override it by including 'user' option which would allow you to normally mount/unmount it from the places menu.

or, another idea would be to remove the entry all together and let gnome handle the mounting

hope that helps

---

### Post by Feilin on 2011-04-27
I deleted the line et voila; problem solved. I'm not sure why, but nevertheless, many thanks!

---

### Post by ~Plue on 2011-04-27
glad it got sorted out :smile:
 remember to mark the thread as solved

---

### Post by plantman on 2011-05-12
I have a related issue. I get an error: filesystem could not be mounted. I have recently upgraded to 11.04. I also got an error: mount point /proc/bus/usb does not exist. Here is what I see in gedit for fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d58a25c4-f965-4d6d-9184-6c8e20d93d77 none            swap    sw              0       0
none /proc/bus/usb usbfs devgid=46,devmode=666 0 0

I am very new to Linux so I need very simple directions. Thanks

---

### Post by plantman on 2011-05-12
No help needed now. I commented out the last line "none /proc/bus/usb usbfs devgid=46,devmode=666 0 0" and it reboots with no problem.

---

