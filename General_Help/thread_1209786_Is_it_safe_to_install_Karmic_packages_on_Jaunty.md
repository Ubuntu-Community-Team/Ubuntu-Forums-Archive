---
title: "Is it safe to install Karmic packages on Jaunty?"
date: 2009-07-10
forum: General Help
---

### Post by veggen on 2009-07-10
I know it used to be unsafe to write to NTFS without ntfs-3g. Is it still so, and if yes, does Ubuntu include ntfs-3g or should it be downloaded separately?

Thanks

---

### Post by drs305 on 2009-07-10
Absolutely safe (as much as can be said of most filesystems), and ntfs-3g is installed on later releases, including jaunty. To put NTFS partitions into fstab, install "ntfs-config" and then System Tools, NTFS Configuration tool to automatically add an entry to fstab so it automounts on boot.

[MountingWindowsPartitions/ThirdPartyNTFS3G]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

---

### Post by t0p on 2009-07-10
```
t0p@ubunty:~$ which ntfs-3g
/bin/ntfs-3g

```

It is perfectly safe to write to NTFS.  A few releases ago ntfs-3g was new and potentially problematic.  But it is now stable, which is why it is now installed with ubuntu by default.

---

### Post by veggen on 2009-07-10
Wow, you guys are fast! Thanks a lot for the info!

---

