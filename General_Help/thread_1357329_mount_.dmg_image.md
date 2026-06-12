---
title: "mount .dmg image"
date: 2009-12-17
forum: General Help
---

### Post by kpholmes on 2009-12-17
im trying to mount a hard disk image, the hd wasa in apples hfs format and has the extension .dmg ; i have hfsplus and hfs utilities installed but when i run the command

 sudo mount -o loop -t hfs iphone-user.dmg /dev/hda2

i get this back 

mount: mount point /dev/hda3 does not exist
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


when i run,
sudo mount -o loop -t hfs iphone-user.dmg /dev/sda2

i get this back

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

i ran dmesg | tail, and got this

kevin@mint-desktop ~/Desktop $ dmesg | tail
[  259.376969] sd 8:0:0:0: [sdb] 3935232 512-byte logical blocks: (2.01 GB/1.87 GiB)
[  259.377714] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  259.379089] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  259.379092]  sdb: sdb1
[  276.534203] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 3384.513806] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 3384.513813]  sdb: sdb1
[ 3812.694793] hfs: can't find a HFS filesystem on dev loop0.
[ 3867.801647] hfs: can't find a HFS filesystem on dev loop0.
[ 3917.069014] hfs: can't find a HFS filesystem on dev loop0.


can anyone shed some light on this please? :P

---

### Post by guga31bb on 2009-12-18
> **kpholmes said:**
> im trying to mount a hard disk image, the hd wasa in apples hfs format and has the extension .dmg ; i have hfsplus and hfs utilities installed but when i run the command

 sudo mount -o loop -t hfs iphone-user.dmg /dev/hda2

i get this back 

mount: mount point /dev/hda3 does not exist
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


when i run,
sudo mount -o loop -t hfs iphone-user.dmg /dev/sda2

i get this back

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

i ran dmesg | tail, and got this

kevin@mint-desktop ~/Desktop $ dmesg | tail
[  259.376969] sd 8:0:0:0: [sdb] 3935232 512-byte logical blocks: (2.01 GB/1.87 GiB)
[  259.377714] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  259.379089] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  259.379092]  sdb: sdb1
[  276.534203] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 3384.513806] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 3384.513813]  sdb: sdb1
[ 3812.694793] hfs: can't find a HFS filesystem on dev loop0.
[ 3867.801647] hfs: can't find a HFS filesystem on dev loop0.
[ 3917.069014] hfs: can't find a HFS filesystem on dev loop0.


can anyone shed some light on this please? :P

Same problem here.

---

### Post by gizmobay on 2009-12-19
I can't get it to work either as I'm getting the same errors as the posters above. I've tried two dmg files and both of them give errors. Here's link to one of the files I tried.

[http://mac.softpedia.com/get/Video/Apple-Shake.shtml](http://mac.softpedia.com/get/Video/Apple-Shake.shtml)

---

### Post by guga31bb on 2009-12-19
FWIW I renamed the file to *.iso and it worked.

---

### Post by gizmobay on 2009-12-19
I ended up converting to an image and then mounting.

[https://help.ubuntu.com/community/DMG2IMG](https://help.ubuntu.com/community/DMG2IMG)

and then mounting the img file.

---

