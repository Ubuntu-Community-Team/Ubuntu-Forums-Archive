---
title: "Grub 2 question"
date: 2011-04-28
forum: General Help
---

### Post by grizzly on 2011-04-28
500Gb hdd - 100mb ntfs , 100mb ubuntu, 300 mb unallocated. Everything running fine; dual booting via grub.

Boot into windows > create a new partition from the unallocated space. Reboot and poof! grub fails . 
This happened to me twice. is it me missing something obvious or is this a major fault in grub 2? I don't remember anything similar happening with earlier grub legacy or lilo.

---

### Post by Leppie on 2011-04-28
you could file a bug?

have you tried creating the partition in ubuntu and then format it in windows?

---

### Post by Lateralis on 2011-04-28
Hmmm... strange.  Not heard of this one before.  What exactly is the error that you get?  Has grub been deleted or can grub just not find the boot files?  

Either way, it may be useful for you to download, run in a Live session and post the result of the [ this boot info script]("http://sourceforge.net/projects/bootinfoscript/").

---

### Post by oldfred on 2011-04-28
While grub uses UUID, it still needs a valid partition table. Some versions of Windows have been known to not rewrite partition table correctly. It may be related to windows not seeing the Ubuntu partitions so it does not add them back into partition table.

Look at this before & after.

sudo fdisk -lu
or 
sudo parted /dev/sda unit s print

---

