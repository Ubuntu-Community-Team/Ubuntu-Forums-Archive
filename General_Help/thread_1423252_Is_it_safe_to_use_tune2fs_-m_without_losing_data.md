---
title: "Is it safe to use tune2fs -m without losing data?"
date: 2010-03-06
forum: General Help
---

### Post by 8301 on 2010-03-06
As of a another problem I have I need to reformat my disks. But now when the hard drives are in Ext4 I dont have enough space to backup my data becourse ext4 takes 5% of space to default reserved disk space. 

Translation 1000 decimal gigabytes * 93% = 930 binary gigabytes and 930 * 0,95 = 883,5

thats 116,5 gig gone :lolflag:

So is it safe to use tune2fs -m to remove the 5 % of ext4:s reserved space on the storage space not the system space?

```
sudo tune2fs -m [percentage] [path to device]
```

---

### Post by iponeverything on 2010-03-06
I believe so, I did it on my 1Tb data partition without running into any problem. I changed mine to 1% reserved.

---

### Post by 8301 on 2010-03-06
Hehe "I believed so" isn't the most convincing answer but I will try it out.

---

### Post by .nedberg on 2010-03-06
I have done it several times, with ext3 and ext4. Never had any problems. I keep 1% for system partitions, and 0 for other partitions.

---

### Post by fragos on 2010-03-07
When I'm concerned about space on a small storage device I use ext2 on it.

---

