---
title: "Command line tool to get mounted directory base on uuid"
date: 2012-02-05
forum: General Help
---

### Post by kamelie1706 on 2012-02-05
hi,

is there an easy command to get the current directory a device is mounted based on its uuid?

"blkid" returns only the device information (/dev/sdx) and works only with "sudo"
"mount" returns only the information if the device was mounted with the UUID

Thanks

---

### Post by dcstar on 2012-02-06
> **kamelie1706 said:**
> hi,

is there an easy command to get the current directory a device is mounted based on its uuid?

"blkid" returns only the device information (/dev/sdx) and works only with "sudo"
"mount" returns only the information if the device was mounted with the UUID

Thanks

**mount** will return the device, this will show the UUID-device links:

```
ls -al /dev/disk/by-uuid
```

---

### Post by kamelie1706 on 2012-02-13
Thanks,

but you still need to guess the mount point.

Is there a "|" combination possible?

---

### Post by Morbius1 on 2012-02-14
```
blkid -o list
```

---

