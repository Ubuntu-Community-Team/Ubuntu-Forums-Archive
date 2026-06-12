---
title: "Can't mount cdrom"
date: 2010-05-20
forum: General Help
---

### Post by kirlian on 2010-05-20
Hi,

after upgrading to lucid i can no longer mount cdrom

fstab looks like this

/dev/scd0                                       /media/cdrom0  subfs   noauto,user,fs=cdfss,ro,procuid,nosuid,nodev,exec  0  0

the error is: mount: unknown filesystem type 'subfs'

when i changed to udf,iso9660 the error was:

mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

thanks for any help.

---

### Post by kirlian on 2010-05-27
anyone?

---

