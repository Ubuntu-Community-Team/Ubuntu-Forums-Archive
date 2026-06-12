---
title: "GRUB Error 17 &amp; NTFS signature missing"
date: 2010-03-02
forum: General Help
---

### Post by johnnyboy66 on 2010-03-02
Power went out and my Linux media server went down. It's basic Ubuntu 8.10 installation. Now when I try to boot it I get GRUB error 17. So I searched the forum, downloaded Ubuntu 9.01 Alternate Live CD to get to terminal and tried mbwardled's solution at [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945). The problem is that when I try to mount /dev/sda1 so that I could edit grub files, it refuses to mount because "NTFS signature is missing". Weird thing is that it's not NTFS formatted drive so I have no idea what to try next.

It seems to me that there's something wrong with partitioning. Anyway to fix it?

I would prefer not to format it because there's some MySQL tables that I would like to keep.

fdisk -l says:
```

Device          Boot       Start          End       Blocks       Id     System
/dev/sda1         *            1          8545      68637681     83     Linux
/dev/sda2                   8546          9964      11398117+    82     Linux swap / Solaris

```

---

### Post by psusi on 2010-03-02
So don't try to mount it as NTFS then?

---

### Post by johnnyboy66 on 2010-03-02
> **psusi said:**
> So don't try to mount it as NTFS then?
I don't. I just use mount /dev/sda1 /ubuntu but for some reason it automatically tries to mount it as NTFS?

---

