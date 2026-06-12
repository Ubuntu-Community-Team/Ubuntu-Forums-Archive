---
title: "Fsck runs every boot"
date: 2011-08-22
forum: General Help
---

### Post by AlexanderDGreat on 2011-08-22
Hi everyone, I would just like to continue this thread.

Here's my partitions:

/dev/sda1 - dual boot with Windows XP, then /boot /swap /root ext4
/dev/sdb1 - /home ext4
/dev/sdc1 - /backups ext4

Now, my problem is this EVERY TIME I login to my Ubuntu machine, it always says

Errors were found while checking the disk drive for / /home /backups /boot

I wonder why this is happening.

Before it doesn't do this. Now it acted strangely. I used the suggestion here to set FSCK=yes but isn't that dangerous?

I'm really confused and scared that one day my machine might SUDDENLY STOP working.

Any help guys? Thanks.

---

### Post by CharlesA on 2011-08-22
Run fsck on those drives from a livecd.

```
sudo fsck /dev/sdxy
```

---

### Post by AlexanderDGreat on 2011-08-22
Thanks CharlesA. I'll turn OFF FSCK=yes, and do as you said. Report back soon.

---

