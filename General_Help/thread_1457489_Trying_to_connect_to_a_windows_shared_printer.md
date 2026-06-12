---
title: "Trying to connect to a windows shared printer"
date: 2010-04-18
forum: General Help
---

### Post by m00nshine on 2010-04-18
Hey all,

Just trying to follow this [howto]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")

I'm having problems with mounting my fstab

I'm getting this when I run sudo mount -a :

[mntent]: line 15 in /etc/fstab is bad

The following is the text of my /etc/fstab :

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=89550585-59a1-420a-a6b5-c2c973f6cf1a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f7476b65-a8b8-4a7a-8666-5d9a2f703e30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
SERVER=home SHARE=Printer MOUNTPOINT=//home/Printer FS_TYPE=smbfs SMB_CREDENTIALS=~/.smbcredentials UID=1000

```Please help!

Thanks,
-m00nshine

---

### Post by m00nshine on 2010-04-19
OK, nevermind that nonsense. I added the printer through System > Administration > Printing. I have a psc 1210 but the wizard only has drivers for a 1200. When I send a print job it does nothing. Can I find the ppd file on the net somewhere or is there a way to make hplip see my printer? It's connected to a computer running xp home and it's shared. Please help!!!!!!!

---

### Post by m00nshine on 2010-05-21
BUMP Please help!

---

