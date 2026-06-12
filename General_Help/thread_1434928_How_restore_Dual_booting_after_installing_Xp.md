---
title: "How restore Dual booting after installing Xp ??"
date: 2010-03-20
forum: General Help
---

### Post by mahmoud fayed on 2010-03-20
[LEFT]hi all  i want to restore grub after installing xp 
my ubuntu version is 9.10 
i had used this        **find /boot/grub/stage1 ........ **
with the previous versions but it didn't work with 9.10
what can i do ??

**thanks ..**
[/LEFT]

---

### Post by ubunterooster on 2010-03-20
Hello and welcome. I keep a liveCD called SystemRescueCD for many problems, including the need to reinstall grub.

---

### Post by 2hot6ft2 on 2010-03-20
Using Ubuntu 9.10 livecd

Here assuming the Ubuntu partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).

Boot up ubuntu from the livecd,open terminal and run:
To find out what your partitions are run
```
fdisk -l
```
then using that info run
```
sudo -i
```
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
```
```
grub-install --root-directory=/mnt/ /dev/sda
```
From the Grub 2 Guide link in my sig.

---

### Post by ubunterooster on 2010-03-21
Oops, you'll likely want links:

[ official site ]("http://sysresccd.org")
[ what wikipedia says about it ]("http://en.wikipedia.org/wiki/SystemRescueCD)
[ another very good site's take ]("http://distrowatch.com/table.php?distribution=systemrescue)

---

### Post by ubunterooster on 2010-03-21
> **2hot6ft2 said:**
> Using Ubuntu 9.10 livecd

Here assuming the Ubuntu partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).

Boot up ubuntu from the livecd,open terminal and run:
To find out what your partitions are run
```
fdisk -l
```
then using that info run
```
sudo -i
```
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
```
```
grub-install --root-directory=/mnt/ /dev/sda
```
From the Grub 2 Guide link in my sig.
Good. Your way is correct also. [I didn't see it till I put in my second  post, though.]

---

### Post by mahmoud fayed on 2010-03-23
[SIZE=3]=D> very thanks :D
[/SIZE]

---

