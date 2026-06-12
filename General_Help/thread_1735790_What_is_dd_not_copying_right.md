---
title: "What is dd not copying right?"
date: 2011-04-21
forum: General Help
---

### Post by ericsonp on 2011-04-21
I have a Dell laptop with a 160GB drive. It has 3 partitions:

/dev/sda1   /boot ext2
/dev/sda3   /     LUKS encrypted
/dev/sda5   swap  LUKS encrypted

I need to swap the drive for another 160GB drive. I put the new drive in an external case and boot a LiveCD and do:

```
sudo dd if=/dev/sda of=/dev/sdb
```

(/dev/sdb is the new drive)

Then I swap the new drive back in for the old and boot and the system does ask for the two LUKS passwords (for swap and /). But then it hangs with the Caps & Scroll lock indicators flashing.

When I put the old drive back and boot it and put the new drive in a case and plug it in, the two drives look identical. I can't even mount both / partitions at the same time, I'm guessing because the UUIDs are identical?

So what did dd not copy or copy wrong? Why can't the cloned, encrypted drive boot?

I tried copying the partition table using sfdisk and refreshed the MBR with:

```
dd if=backup.mbr of=/dev/sdb block=512 count=1
```

(When the new drive is /dev/sdb)

---

### Post by TeoBigusGeekus on 2011-04-21
It could be that the UUIDs are not identical in the end.
Check them with blkid and correct your fstab - if you're using UUIDs at all in it.

---

