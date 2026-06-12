---
title: "Where is partition?"
date: 2010-05-03
forum: General Help
---

### Post by Tux118 on 2010-05-03
Dear Ubuntu forums,

I have recently created a new partiton for LFS (linux from scratch), and now I need to place files on it. The problem is, I do not know where to find it!

I have looked in /mnt and /media and I am currently using ubuntu 10.04 LTS. I created the partition with Gparted.

If any of you could help me solve this, it would be a great help!

---

### Post by notceecee on 2010-05-03
```
sudo fdisk -l
```

---

### Post by Tux118 on 2010-05-03
> **notceecee said:**
> ```
sudo fdisk -l
```

alright, it says it is in /dev

I went and looked in there, but I cannot find sda3

---

### Post by notceecee on 2010-05-03
You need to mount it first.

```
sudo mount /dev/sda3 /mnt
```

---

### Post by dino99 on 2010-05-03
> **Tux118 said:**
> alright, it says it is in /dev

I went and looked in there, but I cannot find sda3

not so clear to me: " I am currently using ubuntu 10.04 LTS " ?

if you want to know about your partitions: install mountmanager, it will give you info about them

or if you have booted on cd, then gparted show the partitions also, just dont do anything else with gparted of course

---

### Post by Tux118 on 2010-05-03
> **notceecee said:**
> You need to mount it first.

```
sudo mount /dev/sda3 /mnt
```

Ah, thank you, now whatever I put in /mnt while it is mounted will go onto the partition, right?

Thanks for your help, I feel stupid :P

---

