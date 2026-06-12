---
title: "how to check what is the OS format?"
date: 2011-07-12
forum: General Help
---

### Post by adhg on 2011-07-12
Hi there, 

can anyone advise how can I check what is the format (FTS/NFTS) my ubuntu is using? I need to ensure that mysql db can grow above 4gb. 

Thanks!

---

### Post by FormatSeize on 2011-07-12
Extension Four is the default. If you didn't change it (I'm sure you didn't if you are asking this question), then that is what it will be. 

Or you can go to a terminal and type
```
cfdisk
```
(NOT AS ROOT!) and it will show you your partition table, which will have that information.

---

### Post by Morbius1 on 2011-07-12
```
sudo blkid
```
If you've been doing a lot of partitioning and changing things around then:
```
sudo blkid -c /dev/null
```

---

### Post by Gyokuro on 2011-07-13
mount can be useful too

---

