---
title: "can't mount LVM snapshot"
date: 2010-02-02
forum: General Help
---

### Post by omnivagus on 2010-02-02
On Ubuntu karmic server AMD64 I want to backup a LVM partition:

```
sudo lvcreate -l12800 -s -nkillme-snapshot /dev/solarium/killme
```

**lvscan**
```
ACTIVE   Original '/dev/solarium/killme' [50.00 GB] inherit
ACTIVE   Snapshot '/dev/solarium/killme-snapshot' [50.00 GB] inherit
```

When I try to mount the snapshot
```
sudo mount /dev/solarium/killme-snapshot /mnt/killme-snapshot
```

I get
```
mount: you must specify the filesystem type
```

What's wrong here?

---

