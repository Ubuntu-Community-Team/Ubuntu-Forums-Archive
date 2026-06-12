---
title: "more than one live USB into an HDD"
date: 2011-01-12
forum: General Help
---

### Post by fdelval on 2011-01-12
Hello all!

I have been given an external HDD of 50GB, with 2 partitions.


40GB of data and 10 GB with a ubuntu live USB.

I accidentally erased it all before even test it, and i was about to create another one with builtin ubuntu boot disk creator.

For my surprise, it ask me to delete all disk in order to install a boot live USB.

It makes sense i guess, because PC may get confused if the boot with an external hdd has more than 1 partition, but, just in case:

**is it possible to install LIVE USB into more than one partition in the same HDD, and make all of them bootable?**

---

### Post by C.S.Cameron on 2011-01-12
You can boot multiple iso's on the same or different partitions using grub2, see [http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

You should be also be able to boot multiple live distro's on multiple partitions if the paths are defined in grub2.

---

