---
title: "Uninstall 9.10"
date: 2009-12-10
forum: General Help
---

### Post by Dave Otter on 2009-12-10
I have 2 partitions on ,my Hard Drive one loaded with 8.04 and the other with 9.10.
 Is there any way I can uninstall just the partition containing 9.10 leaving 8.04 intact.
   If possible step by step instructions would be  most appreciated.
            Many thanks
                  Dave

---

### Post by raymondh on 2009-12-10
> **Dave Otter said:**
> I have 2 partitions on ,my Hard Drive one loaded with 8.04 and the other with 9.10.
 Is there any way I can uninstall just the partition containing 9.10 leaving 8.04 intact.
   If possible step by step instructions would be  most appreciated.
            Many thanks
                  Dave

1.  Back-up your valuable files
2.  Boot into the liveCD (any version but I prefer 8.04 as you *might want* to re-install GRUB).  Go live session (try ubuntu without changes). Going live session will, by default, unmount the partitions to allow you to work on them.
3.  Access gparted (system > admin > partition editor)
4.  Double-check that the partitions are unmounted by right-clicking each partition and, if given the option to unmount, do so.  For swap, select SWAPOFF.
5.  **Identify/verify** the 9.10 partition.  Click to highlight said partition.
6.  Select DELETE amongst the tools.
7.  You may also resize the remaining partitions to occupy the deleted 9.10 partition.
8.  Review and apply.  This may take a while depending on the size of your HD, etc.
9.  Exit gparted and access a terminal if you want to reinstall GRUB-legacy.  You may choose to retain GRUB2 which would be the default bootloader when you installed Karmic.
*  here is a link to [re-install GRUB-legacy]("http://ubuntuforums.org/showthread.php?t=224351")
* If you decide to retain GRUB2, you will have to edit the grub.cfg file to remove the old 9.10 option.  Here is a [link/tutorial by drs305]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305").

If you want, post a screenshot of gparted in your next post and the forum can be more specific with the guide/how-to and identify which partition to remove, how to enlarge the remaining partition, etc.

Have a working/tested back-up of your files.  There are no guarantees when working with partitions.

Happy ubuntu-ing.

---

