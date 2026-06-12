---
title: "Computer doesn't find any bootable devices"
date: 2010-08-05
forum: General Help
---

### Post by Z47isthenew42 on 2010-08-05
I have a Dell Inspiron 1525.  It was a dual boot system between Ubuntu 10.04 and Windows Vista Ultimate.

If I don't boot with a liveCD, I now get a "No bootable devices detected-Strike F1 to retry boot, F2 for setup utility, F5 to run onboard diaganostics" error message and a weird noise.

Both F1 and F2 work, but F5 does nothing.

When I booted into the Ubuntu 10.04 liveCD, the first thing I did was open a terminal and do a ```
fdisk -l
```, but received no output.  I then opened GParted which detected no devices unless I mounted my flash drive.

I then ran the bootinfo script and received this output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

no block devices found 

```

When I pressed F2 to run the setup utility when the error message is displayed, I discovered my BIOS version was A08 (01/07/2008), and then I looked at the Device Info fields, and for some reason it appears that my hard drive is not being detected there either because I saw the following:

```
Primary Hard Drive = {none}
```

I'm hoping there's a way this can be fixed so I can use my laptop again, but I'm not positive if there is any way.

---

### Post by Z47isthenew42 on 2010-08-09
Anyone?

---

