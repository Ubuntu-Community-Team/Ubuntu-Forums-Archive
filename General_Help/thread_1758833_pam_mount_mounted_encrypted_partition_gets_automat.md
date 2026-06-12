---
title: "pam_mount mounted encrypted partition gets automatically unmounted over time"
date: 2011-05-15
forum: General Help
---

### Post by mondalaci on 2011-05-15
/etc/crypttab :
```
storage /dev/sdb none luks, retry=1
```

/etc/security/pam_mount.conf.xml :
```
...
<volume path="/dev/sdb" mountpoint="/storage" cipher="aes-cbc-essiv:sha256" />
...
```

/storage gets mounted upon every reboot and it gets unmounted automatically about 20 minutes later.  /dev/mapper/storage also disappears in such cases.

Nothing gets displayed by dmesg, I'm completely clueless as to why this happens.

Any advice is highly appreciated.

---

### Post by mondalaci on 2011-05-15
Forgot to mention but the mount point also gets removed in such cases.

---

