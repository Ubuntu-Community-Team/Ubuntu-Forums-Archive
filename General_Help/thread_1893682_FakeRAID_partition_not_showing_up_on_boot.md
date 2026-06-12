---
title: "FakeRAID partition not showing up on boot?"
date: 2011-12-10
forum: General Help
---

### Post by GCT on 2011-12-10
So I'm running XUbuntu 11.10 and I'm trying to get a fakeraid drive setup up as just a general use data drive that I can share between my windows and linux installs.  

The device that showed up after I configured things in the BIOS is   
```
/dev/mapper/isw_jbbhieidf_Data0
```

I ran fdisk on that device and created a primary partition, which I then formatted as FAT32.  Once I did this and ran partprobe, I see a /dev/mapper/isw_jbbhieidf_Data0p1 show up. 

I added an entry in my fstab to mount this:
```
/dev/mapper/isw_jbbhieidf_Data0p1 /media/data       vfat auto,users,uid=0,gid=0,fmask=0111,dmask=0,rw   0 0
```

Which works fine if I mount /media/data manually. 

However, if I reboot the system it hangs up and I have to hit S to skip mounting, and investigating the /dev/mapper folder, the p1 device doesn't show up until I manually run partprobe, and then I can mount the drive normally.

Does anyone know why the partition table doesn't seem to be being read on this device on boot?

EDIT: Further hint from running dmraid -aY:

```
$ sudo dmraid -aY
RAID set "isw_jbbhieidf_Data0" already active
ERROR: dos: partition address past end of RAID device

```

---

### Post by GCT on 2011-12-10
I solved this by editing my partition table and just dropping a handful of sectors off the end value.  There must be a bug in how the partition size is calculated...

---

