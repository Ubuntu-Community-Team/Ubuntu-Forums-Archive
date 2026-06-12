---
title: "Black screen after &quot;grub loading&quot;"
date: 2011-02-02
forum: General Help
---

### Post by martvefun on 2011-02-02
Hello,

After a cleaning in my partition table (too many partitions unused) with parted magic livecd, I needed to reinstall grub2 (as partitions had moved).
I did it with the following command :
```
grub-install --root-directory=/media/sda9 /dev/sda
```(where sda9 is my ubuntu partition where grub is installed and /media/sda9 the mount point of this partition)

After a reboot, I had the message "grub loading, welcome to grub" (as usual) but after, instead of having the list of grub entries, I had a black screen.

As I intended to, I installed Debian on another partition with separate boot and rewrited the mbr. Same result...
It seems the computer is working because the fan of my laptop starts is loader than usually.

Any idea ?

Thanks

edit : ok I tried again the command grub-install and it works...

---

