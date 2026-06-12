---
title: "Linux native Volume 2.dsk ???"
date: 2009-10-10
forum: General Help
---

### Post by jdackle on 2009-10-10
Hi everyone,

I'm using a NTFS partition as a data folder for both my Ubuntu 9.04 and Windows Vista.

My fstab:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                                     0  0  
# / was on /dev/sda8 during installation
UUID=fa39aab3-3782-4e52-9e4d-01e4ea254ae2  /              ext3         relatime,errors=remount-ro                   0  1  
# swap was on /dev/sda6 during installation
UUID=b2fe268e-bd48-11dd-ae88-8bee5cb0ebde  none           swap         sw                                           0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                        0  0  

#
# jdackle: Start
#
# /media/Users for user with NUID=1000:
UUID=B892DAA092DA6304	/media/Users	ntfs-3g uid=1000,gid=1000,fmask=0117,dmask=0007,relatime,streams_interface=windows,nodev,noexec,rw,errors=remount-ro,owner

#
# Other partitions:
#
# Windows_Vista:
UUID=0B986DD31139FB13	/media/Windows	ntfs-3g uid=0,gid=0,fmask=0117,dmask=0007,relatime,streams_interface=windows,nodev,noexec,rw,errors=remount-ro,nouser
#
# HP_Recovery
UUID=2C88743C8874071C	/media/HP-Recovery	ntfs-3g uid=0,gid=0,fmask=0117,dmask=0007,relatime,streams_interface=windows,nodev,noexec,rw,errors=remount-ro,nouser
#
# Outro sistema Linux
UUID=c7c7e608-a5ad-470e-9a78-19753432fb0b	/media/Linux		ext3	relatime,rw,errors=remount-ro,nouser,nosuid,nodev,uhelper=hal,grpid
#
# jdackle: End
#/dev/sda7                                  /media/Linux   ext3         errors=remount-ro,nosuid,noexec,grpid,nodev,relatime  0  0 
```

Yesterday I noticed this 1,5GB file on /media/Users:
```
$ ls -nh /media/Users/Linux\ native\ Volume\ 2.dsk 
-rw-rw---- 2 1000 1000 1,5G 2008-11-25 04:43 /media/Users/Linux native Volume 2.dsk
```
Agreed, I don't go to the root of that partition any often, so it could have been there for weeks or even months!... But that's not my point. My point is:
**WTH is that huge file???**:confused:
And... can I delete it? :P

TIA

---

### Post by jdackle on 2009-10-17
Bump.

Anyone...?

---

### Post by Flos Headford on 2010-10-22
I would also like this info.
Phil

---

