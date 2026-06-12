---
title: "Re-partitioning my harddisk"
date: 2006-05-11
forum: General Help
---

### Post by niels on 2006-05-11
Hi there

I want's to repartition my harddisk. At the moment the disk-table looks as follow (some of it is in danish, but I hope you get the point):
Disk /dev/hda: 80.0 Gb, 80026361856 byte
255 hoveder, 63 sektorer/spor, 9729 cylindre
Enheder = cylindre af 16065 * 512 = 8225280 byte

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/hda1   *           1        9352    75119908+  83  Linux
/dev/hda2            9353        9729     3028252+   5  Udvidet
/dev/hda5            9353        9729     3028221   82  Linux swap / Solaris
niels@nielslaptop:~$

I would like to have a partition for my media-files like mp3's and photos. I have tought about 30 GB for this partition. Then I need a backup partition for my document ect. when I have to reinstall or something. I thougt this could be about 5 BG (or it might be a part of the media-partition?). Then I would like a partition for trying out new distros and the development-releases - 10 BG for this one.
What do you think about this?

The big question is - how do i make the artitions? It would be nice if I could use GParted, but I am not afraid of the terminal...

Niels

---

