---
title: "Grub2: how to exclude a drive from update-grub's automatic kernel scan?"
date: 2011-05-01
forum: General Help
---

### Post by dwasifar on 2011-05-01
I have a machine with an external USB backup drive containing images of the primary internal hard drive.  They are true images of the /dev/sda1 partition and are kept in sync with it using rsync.  The idea is that if I have a drive failure I can swap in the most recent backup partition and be good to go.

The problem: any time I do any change that involves running update-grub, such as a kernel update, the kernels on those backup partitions are picked up by update-grub and put in the GRUB boot list.  This results in two undesired effects:

1) The startup default kernel choice no longer works, and the GRUB screen waits until it gets a manual entry.

2) If you pick the wrong manual entry, you boot from the external drive.

The only workaround I've come up with is to physically switch off the external drive before running update-grub or any process that calls it.  This works, but it makes remote administration of updates impossible.  Plus which, I usually forget to do it.

Is there a way to edit the grub2 config files to say "don't scan /dev/sdb"?  I'd expect it to be in the 10_linux file but the syntax in there is over my head.

---

### Post by dwasifar on 2011-05-03
bump

---

### Post by dwasifar on 2011-05-22
bump.  Surely SOMEONE knows.

---

### Post by linuxinstalledfromhdd on 2011-05-22
bump

---

### Post by katykat on 2011-05-23
[http://ubuntuforums.org/showthread.php?p=8871846](http://ubuntuforums.org/showthread.php?p=8871846)

Make sure to look at page 2.

---

