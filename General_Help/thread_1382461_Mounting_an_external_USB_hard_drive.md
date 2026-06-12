---
title: "Mounting an external USB hard drive"
date: 2010-01-16
forum: General Help
---

### Post by enigmaingr on 2010-01-16
Hello,

I'm trying to get ubuntu 9.04 to recognize a Maxtor One Touch III USB external hard drive.  This drive has been formatted and used on a Windows XP.  I cleared everything off but am trying to see if I can arrange it so that I can back up from linux and access (if need be) from a Windows machine.  

Here is what I get with fdisk -l:

/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris

Any help would be greatly appreciated.

---

### Post by StOoZ on 2010-01-16
what size the hard drive is?

type in the terminal
df -h

and pate the output here.

---

### Post by enigmaingr on 2010-01-17
It's a Maxtor One Touch II with 320GB capacity.  Here is the result from df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             109G   12G   92G  11% /
tmpfs                 498M     0  498M   0% /lib/init/rw
varrun                498M  116K  498M   1% /var/run
varlock               498M     0  498M   0% /var/lock
udev                  498M  144K  498M   1% /dev
tmpfs                 498M   84K  498M   1% /dev/shm
lrm                   498M  2.2M  496M   1% /lib/modules/2.6.28-17-generic/volatile

---

### Post by johnnynb on 2010-01-17
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by enigmaingr on 2010-01-17
Here is what I get when I run dmesg:

[  307.641598] scsi 4:0:0:0: Direct-Access     Maxtor   OneTouch III     0338 PQ: 0 ANSI: 4
[  307.689706] sd 4:0:0:0: [sdb] Unit Not Ready
[  307.689711] sd 4:0:0:0: [sdb] Sense Key : Data Protect [current] 
[  307.689715] sd 4:0:0:0: [sdb] <<vendor>> ASC=0xf0 ASCQ=0x1ASC=0xf0 ASCQ=0x1
[  307.691036] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[  307.691697] sd 4:0:0:0: [sdb] Write Protect is off
[  307.691702] sd 4:0:0:0: [sdb] Mode Sense: 57 00 00 00
[  307.691705] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  307.696327] sd 4:0:0:0: [sdb] Unit Not Ready
[  307.696332] sd 4:0:0:0: [sdb] Sense Key : Data Protect [current] 
[  307.696337] sd 4:0:0:0: [sdb] <<vendor>> ASC=0xf0 ASCQ=0x1ASC=0xf0 ASCQ=0x1
[  307.697081] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[  307.697956] sd 4:0:0:0: [sdb] Write Protect is off
[  307.697961] sd 4:0:0:0: [sdb] Mode Sense: 57 00 00 00
[  307.697964] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  307.697972]  sdb:<6>sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIV

---

### Post by enigmaingr on 2010-01-18
> **johnnynb said:**
> [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
The mount instructions did not work for me.

---

### Post by enigmaingr on 2010-01-18
Problem fixed!  I foolishly had the security features enabled; this is why ubuntu didn't mount the drive.  On a Windows machine, I disabled the security.  The drive is now read and writable.  Thanks!

---

