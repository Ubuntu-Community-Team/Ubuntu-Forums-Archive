---
title: "Need help formatting hard drive to NTFS"
date: 2011-09-10
forum: General Help
---

### Post by ZukeisPro on 2011-09-10
Im using just the regular "Disk utility" to try and format and I keep getting this 


/dev/sda1 is mountedand THE DEVICE IS BUSY

So I try and unmount it and I this 


Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=b93c1973-b3ad-4b5b-a3a7-60168b9556cc from /


I've tryed while being Root and still nothing works.

Pleae help!

---

### Post by Enigmapond on 2011-09-10
Why are you attempting to format NTFS? If this is an Ubuntu partition, it's certain death. Did you mean ext4 perhaps?

---

### Post by papibe on 2011-09-10
Could you post the result of these two commands?
```
$ sudo mount -l

$ sudo fdisk-l
```
Regards.

---

### Post by ZukeisPro on 2011-09-10
Im going back to windows and my friend has a Vista CD I tryed installing with it but it said I need to format my hard drive to NTFS.


and here's the results 
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/zuke/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zuke)
/dev/sr0 on /media/CD_ROM type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500) [CD_ROM]

Sudo Fdisk-l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d219c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19076   153219072   83  Linux
/dev/sda2           19076       19458     3068929    5  Extended
/dev/sda5           19076       19458     3068928   82  Linux swap / Solaris
zuke@zuke-KT526AA-ABA-SR5505F:~$

---

### Post by papibe on 2011-09-10
> **ZukeisPro said:**
> Im going back to windows and my friend has a Vista CD I tryed installing with it but it said I need to format my hard drive to NTFS.
I understand now.

You can't format your whole drive because you are using it.

Boot into the Ubuntu install CD, but instead of install it, choose the option "Try it first" or "Ubuntu Live". Once you get into the desktop look for the program Gparted in the menus. Using that you can format the whole drive back to NTFS.

Note that you will erase ALL your data with this procedure. If you need to save files do it before this.

Hope it helps,
Regards.

---

### Post by raja.genupula on 2011-09-10
you can use disk utility also for formatting the drive . its a  easy method

---

### Post by papibe on 2011-09-10
> **raja.genupula said:**
> you can use disk utility also for formatting the drive . its a  easy method
+1

Actually it could be easier than Gparted! (Disk Utility will be also available on the Live CD).

Regards.

---

### Post by Mark Phelps on 2011-09-10
A better solution is to use the Gnome Partition Editor, run from the CD, to remove ALL the Linux partitions on the drive and then -- NOT format it.

When you boot from the Vista disk, it will give you the option of formatting your disk (or the unused space, if there are other partitions on the drive).  Let Vista do its own formatting.

---

### Post by raja.genupula on 2011-09-10
> **Mark Phelps said:**
> A better solution is to use the Gnome Partition Editor, run from the CD, to remove ALL the Linux partitions on the drive and then -- NOT format it.

When you boot from the Vista disk, it will give you the option of formatting your disk (or the unused space, if there are other partitions on the drive).  Let Vista do its own formatting.

hwy mark phelps 

i think disk utility  can do that also just deleting the partition , make free space . please suggest me back if this thing not gonna work .

---

### Post by Mark Phelps on 2011-09-11
> **raja.genupula said:**
> hwy mark phelps 

i think disk utility  can do that also just deleting the partition , make free space . please suggest me back if this thing not gonna work .

Don't use Disk Utility; prefer GParted.  But, if Disk Utility will let you remove all the Linux partitions, then you can use it -- but you will have to be running in LiveCD mode.

---

### Post by raja.genupula on 2011-09-11
hey , thank you very much.
thanks for suggesting me back .

---

