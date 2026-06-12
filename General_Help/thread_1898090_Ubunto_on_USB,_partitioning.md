---
title: "Ubunto on USB, partitioning"
date: 2011-12-20
forum: General Help
---

### Post by webmanoffesto on 2011-12-20
I'm working to put Linux on a USB Disk on Key. One is Ubuntu. When installing Puppy Linux it suggested that I partition the DoK. I managed to use GParted to partition the Disk on Key and Flag a partition as Boot partition. With Ubuntu, either it didn't suggest partitioning or I just didn't do that.

I'm confused. I like the benefit of having a system partition and a data partition. But when I later boot Windows, Windows doesn't recognize the second partition. What do you recommend?

---

### Post by oldfred on 2011-12-20
Windows only sees a first partition on a USB flash drive if it is FAT or NTFS.

Are you creating an installer flash drive that you can also run as a liveCD in a 4GB or less or installing the full install in a 8GB or larger flash drive?

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

If installing multiple ISOs to one drive there are now scripts to do that also.

---

