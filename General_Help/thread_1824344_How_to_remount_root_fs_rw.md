---
title: "How to remount root fs rw?"
date: 2011-08-13
forum: General Help
---

### Post by mcemsi on 2011-08-13
After an error on my root fs it had been remountet readonly.


sudo mount -n -o remount, rw /

tells me


Can't open /var/lib/sudo/martin/0: Read-only file system
mount: you must specify the filesystem type


TIA

---

### Post by mcemsi on 2011-08-14
no ideas?

---

### Post by dandnsmith on 2011-08-14
You should have, at the time the error was announced, an instruction to run fsck (with parameters) to clear the errors.
Once that is done, then just reboot and things should be returned to normal.
HTH

---

