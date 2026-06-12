---
title: "hwclock exited with status 2 after partition recovery."
date: 2010-07-24
forum: General Help
---

### Post by ppp0 on 2010-07-24
Hello everybody!
I've recovered partition ext4 and after fixing some errors (fsck.ext4 /dev/sda5) Lucid won't load. It Says: 

hwclock exited with status 2.

How can i trace this error or fix it quickly? I'm in some panic :-/

---

### Post by ppp0 on 2010-07-25
when i chrooted to my old system via livecd (sudo chroot /media/77....) hwclock says:
```

hwclock from util-linux-ng 2.17.2
hwclock: Open of /dev/rtc failed, errno=13: Permission denied.
No usable clock interface found.
Cannot access the Hardware Clock via any known method.
```

---

