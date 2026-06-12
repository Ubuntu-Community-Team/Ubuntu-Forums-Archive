---
title: "Can't mount NAS on boot after upgrade."
date: 2012-05-31
forum: General Help
---

### Post by guyfromfl on 2012-05-31
I have a D-Link NAS321 that used to automount on boot, but stopped after upgrading.  I have cifs, samba and nmbd installed.  I copied the old fstab from the previous install and is below.

I also went through several tutorials and other forum posts but I cannot get any of those methods to work either.

During boot, I get the error "The disk drive for /home/mark/W is not ready yet or not present"...and have to hit S to skip

After I have booted, sudo mount -a will mount the drive.

Anybody have any suggestions? Here is the fstab:

The NAS is the 192.168.0.194 entry...

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
# UUID=125c6c4a-3cc1-4f25-8c7f-10344999dcd2 /               ext4    errors=remount-ro 0       1

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=125c6c4a-3cc1-4f25-8c7f-10344999dcd2 /               ext4    errors=remount-ro 0       1
//192.168.0.194/Volume_1 /home/mark/W cifs credentials=/root/.smbcredentials,uid=1000,gid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
/dev/sda4 /media/Storage ext2 defaults 0 0


UUID=5c335022-9c37-4905-8c69-0b077c0a7e95	/home	ext4	nodev,nosuid	0	2



```

---

### Post by steeldriver on 2012-05-31
I wonder if it is something related to the changeover from traditional /etc/network/interfaces to doing everything via network-manager? 

Possibly the  network-manager service starts later in the boot process and the interface may not be up when it tries to mount - I think the server distributions have stuck with traditional ifupdown maybe for that reason?

---

