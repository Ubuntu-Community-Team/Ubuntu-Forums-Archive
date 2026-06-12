---
title: "how often doues Ubuntu run a routine check of drives?"
date: 2009-08-04
forum: General Help
---

### Post by hihihi100 on 2009-08-04
Hi there:

I logged in 5 mns ago, and the system ran a "routine check of drives".. this is the second time it happens. Isn't it a sign that something's wrong? If so, what should I do?

cheers

---

### Post by NightwishFan on 2009-08-04
No, that is fine. It is designed to do this on every 20 or so mounts to verify filesystem integrity. That is completely normal.

---

### Post by michy99 on 2009-08-04
You can control how often the drives are checked with tune2fs. By default it checks every 30 mounts. To change it to every 50 mounts, you can enter:```
sudo tune2fs -c 50 /dev/sda1
```Of course you would change sda1 to whatever device you want to change.

You can also have it check by time interval instead of number of mounts. To check every 3 days:```
sudo tune2fs -i 3d /dev/sda1
```You can also use w for weeks and m for months.

---

### Post by jocampo on 2009-08-04
> **hihihi100 said:**
> Hi there:

I logged in 5 mns ago, and the system ran a "routine check of drives".. this is the second time it happens. Isn't it a sign that something's wrong? If so, what should I do?

cheers

Every 30 boots or so your system performs what is know as an "fsck" to make sure your hard drive has no error.

To modify please run

```
sudo tune2fs -c 10 /dev/hda1
```

the number indicates how often the check will be executed.1 makes it scan at every boot, 0 stops scanning altogether

---

### Post by jocampo on 2009-08-04
By the way... I think that if you check fstab (the list of mounted partitions), you'll see the default and current values for your partitions ...

---

### Post by martinbaselier on 2009-08-04
All of you are forgetting something it doesn't check every 30 days or every 20 boots or whatever the default values are. It does both. The options to change it are correct. But you would need to change both the time between checks and the number of times you can boot before a check is done.

---

### Post by mcduck on 2009-08-04
> **jocampo said:**
> By the way... I think that if you check fstab (the list of mounted partitions), you'll see the default and current values for your partitions ...

No, the numbers in fstab are for dump and fsck *order* and have nothing to do with the frequency how often fsck is ran.

But if you set the check order (the last number) to "0" that *will* disable checking that partition. (Other options are "1" for root partition which needs to be checked first, and "2" for every other partition you want to check, to check them after the root).

Personally, I always leave it as it is. Spending a minute or two once a month to make sure that all my files are fine doesn't sound too bad to me. Actually the only problem is that fsck checks my Ext4 partitions so quickly I don't have enough time to make a cup of coffee while waiting.. :D

---

### Post by mcduck on 2009-08-04
> **martinbaselier said:**
> All of you are forgetting something it doesn't check every 30 days or every 20 boots or whatever the default values are. It does both. The options to change it are correct. But you would need to change both the time between checks and the number of times you can boot before a check is done.

You can either set the check interval based on time, or based on boot count, but not both. The later setting would just override the first one.

---

