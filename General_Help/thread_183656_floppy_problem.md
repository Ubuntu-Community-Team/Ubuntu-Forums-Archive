---
title: "floppy problem"
date: 2006-05-28
forum: General Help
---

### Post by jim mcalister on 2006-05-28
floppy problem from tjm
have breezy badger 5.10  2-6-12-10-386
was using work around "mount /media/floppy0" ok untill pmount 0.9.6-1~breezy was installed. Now get following errors:

unable to mount selected volume
mount: block device /dev/fd0 is write-protected, mounting read-only
mount: /dev/fd0: can't read superblock

fstab is /dev/fd0        /media/floppy0  vfat,ext2,msdos   rw,user,noauto      0       0

Have tried other fstab <type> and <options> as suggested in the forums

Also tried installing pmount sudo dpkg -i from downloaded pmount_0.9.6-1~breezy1_i386.deb with same results and error messages. Synaptic status shows pmount installed and also shows it in the installed (local or obsolete)

The floppy drive is detected and floppy1 icon appears Places, Computer

any help would be appreciated, thanks

---

### Post by jim mcalister on 2006-06-20
read fourm floppy entries
reinstalled pmount 0.9.6-1~breezy1
reinstalled fdutils 5.5-20050303-1(breezy)
checked permissions
tried various fstab settings
installed mtools
read sys log for I/O error
replaced floppy drive to board cable
all works now
thanks jim
u r welcome jim

---

### Post by ifokkema on 2006-06-20
[QUOTE=jim mcalister]all works now
thanks jim
u r welcome jim[/QUOTE]
LOL, I'd say it was your cable then?

---

### Post by jim mcalister on 2006-07-05
yup, the cable was bad. HA

---

