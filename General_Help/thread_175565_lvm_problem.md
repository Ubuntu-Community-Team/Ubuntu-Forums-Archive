---
title: "lvm problem"
date: 2006-05-13
forum: General Help
---

### Post by linuxgrrl on 2006-05-13
hello,
I am trying to set up lvm to work with my multimedia box.  I'm following the instructions here: [http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html?page=2](http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html?page=2)

Everything seems to work up to creating the filesystem.   mkfs.xfs can't seem to find the logical volume.  if I run "lvdisplay" it seems to be there:

  --- Logical volume ---
  LV Name                /dev/mediavg/videolv
  VG Name                mediavg
  LV UUID                W5moc0-JXQt-8rsh-xeUO-MtYb-NDou-aD8hYS
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                150.00 GB
  Current LE             38400
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:9

My volume group looks OK afaict:

 --- Volume group ---
  VG Name               mediavg
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  2
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               259.59 GB
  PE Size               4.00 MB
  Total PE              66454
  Alloc PE / Size       38400 / 150.00 GB
  Free  PE / Size       28054 / 109.59 GB
  VG UUID               SlwI8w-3o6O-RPtt-52M4-S7JR-wJ52-JFvjgt

But if I run "sudo mkfs.xfs /dev/mediavg/videolv" I get "cannot stat /dev/mediavg/videolv -- file does not exist."

Google no help so far.
thanks for any suggestions,
Mary

---

### Post by linuxgrrl on 2006-05-13
solved my own problem  *sigh*
while installing ubuntu, I had given the partition a label, so it had an /etc/fstab entry. 

This is BAD, because it was mounted when I did all my lvm commands.  I didn't get any warnings, but the LVM commands just didn't "take" until I removed the fstab entry and rebooted and started over.

---

