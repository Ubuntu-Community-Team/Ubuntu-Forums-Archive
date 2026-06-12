---
title: "2TB Raid 1 woes..."
date: 2011-05-26
forum: General Help
---

### Post by FeraTech on 2011-05-26
So I had a 2TB drive fail.

I am using Ubuntu 10.04 LTS x64

I have the following setup.

2x 500GB Raid1 drives mounted /
2x 2000GB Raid1 drives mounted /home

1 TB drive failed. Using Palimset I tried adding the new drive but got the following MDADM error:
Not enough room to add drive to array.

I tried using fsdisk to manually create the partition table but sadly was unable to because fsdisk doesn't support drives over 2TB.

I could not figure out how to do this in parted.


SOOO.....

I decided to do this:

```
sudo mdadm --add /dev/md2 /dev/sdc
```

Instead of creating the patition table I added the core drive and it seems to be syncing.

Should I be worried? Will this work? Please help!

---

