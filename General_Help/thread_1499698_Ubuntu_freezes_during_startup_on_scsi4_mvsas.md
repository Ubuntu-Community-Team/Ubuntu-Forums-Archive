---
title: "Ubuntu freezes during startup on scsi4: mvsas"
date: 2010-06-02
forum: General Help
---

### Post by tshannon on 2010-06-02
Everything was starting up fine, then a few times it would freeze during boot, now every time it freezes during the boot.

I removed quiet, and added nosplash to the grub startup option, and I see that where it waiting is on a line that says:

scsi4 :  mvsas

There is no disk activity at this time, and it'll sit there forever.

---

### Post by tshannon on 2010-08-15
I've been able to get around this by forcing a fsck at each boot.  If I have a boot that doesn't have a fsck, then it won't get past scsi4: mvsas.

fsck doesn't return any errors though, so I'm not sure what the problem is.

---

### Post by tshannon on 2010-09-27
Looks like the latest kernel fixed my issue.  I'm booting up fine now.

---

