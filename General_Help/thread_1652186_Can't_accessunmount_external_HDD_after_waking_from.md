---
title: "Can't access/unmount external HDD after waking from sleep"
date: 2010-12-24
forum: General Help
---

### Post by thesultanofswing on 2010-12-24
I have a WD MyPassport 320GB external hdd and Ubuntu 10.10. The problem is that I can't access my drive after waking from sleep. I can't even unmount it; gives me an error like: "umount: /media/0A26FE8626FE71D5 mount disagrees with the fstab". Any way I can correct this problem?

---

### Post by TeoBigusGeekus on 2010-12-24
Have you tried unmounting it with this
```
sudo umount /media/0A26FE8626FE71D5
```
?

---

### Post by thesultanofswing on 2010-12-24
I did the above ^^ and it unmounted fine. Now if I replug it in, I have to mount it again through the terminal using the mount command. Is there any way that I can avoid this process? I mean not having to remount after waking up?

---

