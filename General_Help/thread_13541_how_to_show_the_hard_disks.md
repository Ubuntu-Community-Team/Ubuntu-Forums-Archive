---
title: "how to show the hard disks"
date: 2005-02-01
forum: General Help
---

### Post by lycos on 2005-02-01
hi,
i am using ubuntu for a few days.
the problem i have, i cant see the particians.
windows disks and the disks without op system e.g.
[the image of it](http://www.geocities.com/saimaktay/EkranGoruntusu.png) 

when i wrote sudo fdisk -l command as you can see below, i can see the disks.
root@ubuntu2:~ # sudo fdisk -l

Disk /dev/hda: 8195 MB, 8195281920 bytes
240 heads, 63 sectors/track, 1058 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         277     2094088+   6  FAT16
/dev/hda2             278        1058     5904360    5  Extended
/dev/hda5             278         480     1531813+   b  W95 FAT32
/dev/hda6   *         481        1008     3991648+  83  Linux
/dev/hda7            1009        1058      377968+   e  W95 FAT16 (LBA)
root@ubuntu2:~ #

when i wrote mount command it is not working.
root@ubuntu2:~ # mount /dev/hda2
mount: can't find /dev/hda2 in /etc/fstab or /etc/mtab
root@ubuntu2:~ #

any suggestion please?
thanks for your help

---

### Post by AlBundy on 2005-02-01
[Ubuntu Starter Guide](http://ubuntuguide.org/#automountfat)

---

### Post by lycos on 2005-02-01
it worked..
thanks a lot  :)

---

### Post by jdodson on 2005-02-01
please understand this is not a place to post questions.  before you post in any forum area please read the rules.  i am redirecting your post to the correct forum area.

---

