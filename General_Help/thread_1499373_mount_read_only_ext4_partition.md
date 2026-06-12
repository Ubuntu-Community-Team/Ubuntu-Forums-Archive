---
title: "mount read only ext4 partition"
date: 2010-06-01
forum: General Help
---

### Post by cccc on 2010-06-01
hi 

I have dual boot: Ubuntu 10.04 and Opensuse 11.2.
Howto mount read only ext4 partition from opensuse in /etc/fstab?

---

### Post by cccc on 2010-06-04
Knows someone?

---

### Post by sisco311 on 2010-06-04
Check out: [thread=283131]Understanding fstab[/thread]

```
UUID=<uuid of the partition>    /media/mount-point    ext4    relatime,ro    0    2
```

---

