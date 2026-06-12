---
title: "I failed at /etc/fstab"
date: 2011-08-30
forum: General Help
---

### Post by KingA on 2011-08-30
I tried to make linux to automatically mount my NTFS volumes and tried to edit the /etc/fstab file.

I added this lines to the file:

```

/dev/sda1	/media/Win	ext4	defaults	0	0
/dev/sda2	/media/D	ext4	defaults	0	0

```

The first one is my Windows boot volume.

So when Ubuntu boots it gives me 2 errors that sda1/2 failed to mount and skipped it.

LE: how do I delete this topic ? lol... I just noticed i tried to mount NTFS volumes using ext4... Sorry :)

---

