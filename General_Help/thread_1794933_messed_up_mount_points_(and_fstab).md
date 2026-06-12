---
title: "messed up mount points (and fstab?)"
date: 2011-07-01
forum: General Help
---

### Post by bringingdadaback on 2011-07-01
During my numerous attempts to set up access to my Windows partition from Ubuntu (all in vain, by the way) I seem to have completely messed up my mount points. When booting up I have to press 'S' to skip mounting, as it can't mount properly on its own.

Here's the contents of my fstab file (which I foolishly neglected to back up):
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc           proc     nodev,noexec,nosuid               0  0  
/host/ubuntu/disks/root.disk  /               ext4     loop,errors=remount-ro            0  1  
/host/ubuntu/disks/swap.disk  none            swap     loop,sw                           0  0  
/dev/sda2                     /media/sda2  ntfs-3g  users                             0  0  
/dev/sda1                     /media/sda1     ntfs     nls=iso8859-1,ro,users,umask=000  0  0  
/dev/sda3                     /media/sda3     ntfs     defaults                          0  0  
/dev/sda4                     /media/sda4     vfat     defaults                          0  0  Any help with fixing the messed up mounting would be greatly appreciated (as would any help with being able to access my Windows partition, after having struggled with it all evening! :().

---

### Post by coffeecat on 2011-07-01
I see you are using wubi. You don't have to mount your Windows partition with /etc/fstab. It's already mounted in /host

Open a nautilus browser and click on "File System" in the left pane and then open the /host folder. That's your Windows partition.

---

### Post by bringingdadaback on 2011-07-01
gee, I could have saved myself quite a bit of trouble with that info.** thank you!**

---

