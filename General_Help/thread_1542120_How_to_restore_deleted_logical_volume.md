---
title: "How to restore deleted logical volume?"
date: 2010-07-30
forum: General Help
---

### Post by eunhyeon on 2010-07-30
I have 3 harddisks, 1 for system and 2 for data.

To manage it more easy, I tied 2 harddisk in LVM. And I made an logical volume. It used ext4 for it's filesystem.

Today, I wanted to format and reinstall the system. So I booted the system using Ubuntu CD.
But managing the partition, I accidently delete the logical volume.
Because backup(/etc/lvm) was in itself, I couldn't restore the old config.
I just create new logical volume.

 As I expected, I couldn't mount it correctly. 
Mount said that "Mount: Mouting failed A on B! Invalid argument!"

I must recover it, because it has a lot of import data.
What should I do?


Thanks.

---

### Post by dino99 on 2010-07-30
[http://www.linuxjournal.com/article/8874](http://www.linuxjournal.com/article/8874)

[http://www.linuxinsight.com/resolving-lvm-metadata-corruption.html](http://www.linuxinsight.com/resolving-lvm-metadata-corruption.html)

[http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/](http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/)

---

