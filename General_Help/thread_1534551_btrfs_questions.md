---
title: "btrfs questions"
date: 2010-07-19
forum: General Help
---

### Post by lexiii on 2010-07-19
I've just converted a ext4 Partition to btrfs. Seems everything is working. But I'm a bit helpless about compression.

This is how I mounted the Partition:
sudo mount -o btrfs /dev/sda7 /media/files

Is it compressed that way? I want the partition to mount on startup, so I've added the following line to fstab:

/dev/sda7 /media/files btrfs rw,user,compress 0 0
It mounts, but I have no idea if it's compressed.

How can I see the compression ratio of a file? Also I have no idea how much space is left on the Partition. df tells me 100% is used.

I only have Media Files on that Partition and I've got the feeling that everything works a bit faster than it did on ext4.

---

### Post by cariboo on 2010-07-20
There is a [btrfs]("http:///ubuntuforums.org/showthread.php?t=1481973&highlight=btrfs") thread in the Maverick Testing & Discussion sub-forum. It may be a better place to ask your questions.

---

