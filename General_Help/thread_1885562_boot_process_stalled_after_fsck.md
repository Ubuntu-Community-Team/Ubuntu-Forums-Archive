---
title: "boot process stalled after fsck"
date: 2011-11-23
forum: General Help
---

### Post by goofrider on 2011-11-23
Someone at my house unplugged the power to my system and now it won't boot. At first I thought it was dirty file system so I removed the drive and fsck everything on a different computer. It still won't boot.

Basically the boot process stalls @:

```

root: clean, nnnnnn/NNNNNN files, nnnnnn/NNNNNN blocks
....

```

After it reports all file systems clean, it stalls. The hard drive spins out of control as if it's doing an fsck but there's no messages, and it already reported all file systems are clean (there's no other file system remaining on that hard drive).

Any idea what the system is doing? 

Anything else I can do short of reformatting the root FS?

---

### Post by goofrider on 2011-11-24
OK my mistake. Looks like a previous release upgrade didn't finish and it might have something to do with it. 

Mounted it on my Mac in a VM, boot from Ubuntu Rescue Remix, chroot to it and did a dpkg --configure -a, but still didn't fix it.

Gonna try to remove some possible offenders (bootchart, mdadm) and do another release upgrade, see if it helps.

---

