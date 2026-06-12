---
title: "Mounted Drives Invisible in terminal AND Nautilus"
date: 2010-01-26
forum: General Help
---

### Post by OlJack on 2010-01-26
I am using Karmic Koala and not finding uniform behavior regarding internal hard drive mounts. I have placed commands in fstab to mount partitions at boot. One a separate hard drive and the other a separate partition on the boot drive that I set up during OS installation. After boot, GParted shows both of these partitions mounted on the right points (in my case, /dd and /opt). Both the mount points have rw permissions for all. But neither "ls -l" in the terminal nor nautilus shows the drives. They are evidently invisible.

I searched the net for hours looking for an answer to this and couldn't find it. Hope someone knows why this is going on.... OlJack[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

---

### Post by diesch on 2010-01-27
What does
```
mount
```
say in a terminal?

---

### Post by OlJack on 2010-01-27
It indicates that the partitions are mounted, same as GParted. 
 
Right now I am reinstalling 9.04 to see if it has the same problems as 9.10. Evidently between these two versions the handling of internal hard drives was changed. For example, without putting anything in fstab ONE but not both of the partitions are shown in the "Places" menu. It appears in the "places" menu automatically but requires a password to be mounted. Placing the mount request in fstab mounts the drive but nothing, including the terminal under sudo can see it.
 
The documentation I have found scouring the forums evidently has not caught up with Karmic...

---

