---
title: "mount error during boot"
date: 2011-02-16
forum: General Help
---

### Post by lucien on 2011-02-16
Hi,

my system randomly stops during boot (I'd say it happens one out of ten times) and says, a partition couldn't be mounted due to "filesystem errors".

This is my drive partitioning:
```

/dev/sda3 on /     type ext4
/dev/sdb2 on /home type ext4
/dev/sdb3 on /var  type ext4

```
Perhaps these mounts are also relevant:
```

tmpfs on /tmp      type tmpfs (rw,nosuid,mode=1777)
none  on /var/run  type tmpfs
none  on /var/lock type tmpfs

```

Booting mostly stops after trying to mount /dev/sdb3, but sometimes after trying /dev/sdb2. So my guess is it happens due to my partitioning-scheme over multiple drives and there is some sort of race-condition.

When I then drop to a root shell and manually do a fsck, no problems are reported and I can resume booting without any issues.

I'm happy to privide further information, and will write down the exact wording of the error the next time it occurs.

Greetings,
lucien

---

