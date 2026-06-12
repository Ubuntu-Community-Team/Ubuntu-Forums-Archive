---
title: "Disk drives randomly checked for errors at startup"
date: 2011-10-04
forum: General Help
---

### Post by rva1945 on 2011-10-04
Sometimes I see this at startup:

Your disk drives are being checked for errors.

Then it reaches 100% and no error messages.

I always close Ubuntu normally (shut down after closing open applications).

Do I worry about anything?

Thanks

---

### Post by drs305 on 2011-10-04
No need to worry. These are automatically scheduled checks run by the system. The default is to check every 30 mounts. The frequency can be changed using options with the *tune2fs* command but most normal users probably don't make any changes. The checks can be disabled by a setting in /etc/fstab but I wouldn't recommend that.

---

