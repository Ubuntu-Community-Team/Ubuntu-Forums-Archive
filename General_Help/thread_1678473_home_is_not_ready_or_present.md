---
title: "/home is not ready or present"
date: 2011-01-30
forum: General Help
---

### Post by terry_opie on 2011-01-30
I've been seeing issues with this for the last few months when getting kernel updates.  Never on every reboot, but this last time has been somewhat stubborn.  Usually I can go back to the previous kernel, boot, reboot and I'm good.  But not this time.

My fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=502c0b6e-8f10-4e88-b44b-65ca0193c3a4 /               ext4    errors=remount-ro 0       1
/dev/sdb1       /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=279222f9-a992-440e-9e1d-2a2353b328e3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
192.168.1.200:/mnt/HD_a2/ /mnt/dns-323_1 nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.200:/mnt/HD_b2/ /mnt/dns-323_2 nfs rsize=8192,wsize=8192,timeo=14,intr

```

UUIDs of the drives:
```
--> sudo blkid -s UUID
[sudo] password for opiet: 
/dev/sdc1: UUID="502c0b6e-8f10-4e88-b44b-65ca0193c3a4" 
/dev/sdc5: UUID="279222f9-a992-440e-9e1d-2a2353b328e3" 
/dev/sdd1: UUID="726b67d7-9b23-4557-9574-64b03739da57" 
```


When I boot with a live CD and check the drives, I noticed that my home partition, which when booting with the live CD is sdb1.  No errors found, everything is fine.

But when I've been booting normally, I notice that everything has moved somewhat...  the drive that used to be sda is now sdc, but is still found on a boot.  My home partition which is on a separate drive, sdb, is now listed as sdd.

I've tried using the UUID in the fstab for my home partition, and that does nothing.  

When it gets to the error message during boot, I can manually mount the drive to /home, using /dev/sdd1.  I then exit the root shell, and get a login.  After that I'm back in business.

I'm a little confused as to why the drives changed device names, and whether anyone has any ideas as to a way to manually get /home mounted automatically.  I can handle the manual steps, but its a pain.

Thanks!!

---

### Post by terry_opie on 2011-01-30
I did just modify my fstab to mount home to /dev/sdd1 and it auto mounted...

One thing I forgot to mention, was that a week ago I finally moved to 10.10.  I have not updated since that update....  at least until this all started anyway.

So, I guess the question I need answered, why with 10.10, did all my devices get switched around?

---

### Post by bdaman80 on 2011-01-30
I didnt notice any different drive references when I upgraded my desktop or Netbook from 10.04 to 10.10

But I have had the problem with not booting a new Kernel from time to time

---

### Post by QLee on 2011-01-30
[QUOTE=terry_opie]...
I've tried using the UUID in the fstab for my home partition, and that does nothing.  
...[/QUOTE]

That should work.

/ and your swap are listed by UUID in your fstab and still work despite the device node changes as you have noticed.

Your /home should work too if you use the correct UUID for the partition that is your /home, it might be worthwhile to verify that you tried the correct UUID.

---

