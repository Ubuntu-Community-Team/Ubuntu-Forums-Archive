---
title: "Routine check of drives"
date: 2009-09-01
forum: General Help
---

### Post by xeriouxi on 2009-09-01
Hi,

Every so often, Ubuntu will do a routine check of my drives when booting up and this happens every 3-4 weeks or so. However, this happened yesterday and I turned my PC on today and it ran again. It completed just fine yesterday so I'm a bit worried as to why it decided to do this again today. Is there any logs that will help me figure out why this happened? Also, is this actually something to be worried about?

Thanks!
Ian.

---

### Post by P4man on 2009-09-01
No, its completely normal. After 30? (not sure) mounts, fsck will be forced to check your filesystem. You can change that behaviour if you want, disable it,  increase the number of mounts. Or better, make it check on shutdown:

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

### Post by StuartN on 2009-09-01
I would not worry, it seems that the check of separate partitions drift out of synch so it probably checked one partition yesterday and a different one today. You can see what was checked most recently with:

```
cat /var/log/fsck/checkfs
```

---

### Post by xeriouxi on 2009-09-01
The only reason I'm worried is because I only have one partition/hard drive... :(

---

### Post by xeriouxi on 2009-09-02
Bump! =)

---

### Post by jjgomera on 2009-09-02
well, its normal too when electric shutdown or hard reboot corrupt filesystem and fsck try to fix, fsck say the reason:
-filesystem have been mounted 30, check forced
-filesystem with error, check forced

i dont worry yet, but if this check repeats often, maybe your harddisk would be close to die

---

### Post by StuartN on 2009-09-03
> **jjgomera said:**
> corrupt filesystem

If there was an error in the file system then fsck would have reported it. If fsck did not report an error then there probably is no error.

For peace of mind, you can list all your partitions with sudo fdisk -l. You can check those partitions by running fsck with the partitions unmounted, i.e. either boot from a CD or enter recovery mode by pressing Esc at the GRUB menu. RescueCD and the like have disk checking GUI software.

---

### Post by xeriouxi on 2009-09-04
Thanks for all your replies! I guess it was just a minor glitch, hehe! :)

---

