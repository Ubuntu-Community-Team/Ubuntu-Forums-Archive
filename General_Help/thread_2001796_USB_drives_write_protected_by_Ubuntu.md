---
title: "USB drives write protected by Ubuntu"
date: 2012-06-11
forum: General Help
---

### Post by barefootninja on 2012-06-11
Hi people
I have now had two USB drives write protected after deleting folders using PP. I know from the forums that other users are having the same problem, and I can't afford to lose drives! Anyone out there able to help? BTW I'm no expert at Terminal! Thanks.

---

### Post by timcowchip on 2012-06-11
Are you meaning USB memory sticks or hard drives? If memory sticks are being write protected, then try this in a terminal

```
sudo fdisk -l
```

with the USB stick inserted.

then 

```
dd if=/dev/zero of=/dev/sd* bs=512 count=4096
```

where * is the letter corresponding to your USB stick in the output of the first command.

for example 

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15681535     7839744    b  W95 FAT32

In this case my USB stick is /dev/sdb. The number 1 refers to a partition on that stick. Don't use the number. You want to wipe out the first 4096 bytes on the stick where write protection would reside. 

so 

```
dd if=/dev/zero of=/dev/sdb bs=512 count=4096
``` 

then use a partitioner like gparted to create a partition table and new partition on your USB stick

You don't have to be an expert. Just copy and paste the code.

---

### Post by barefootninja on 2012-06-11
thanks I'll try that 2moro and let you know how I get on.

---

