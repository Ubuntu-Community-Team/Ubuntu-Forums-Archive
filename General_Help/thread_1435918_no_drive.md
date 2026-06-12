---
title: "no drive"
date: 2010-03-22
forum: General Help
---

### Post by tooler on 2010-03-22
hi i installed ubuntu alongside win 7 ultimate
i installed ubuntu on the slave drive
i have music and pictures folders on the same drive
but when i go into ubuntu i cant see them
as the drive is not visable
can anyone please advise?

---

### Post by plucky on 2010-03-22
> **tooler said:**
> hi i installed ubuntu alongside win 7 ultimate
i installed ubuntu on the slave drive
i have music and pictures folders on the same drive
but when i go into ubuntu i cant see them
as the drive is not visable
can anyone please advise?

Assuming the folders are using NTFS,you have to mount the partitions separately as linux doesn't auto-mount partitions as windows does.

See this [link](http://www.psychocats.net/ubuntu/mountwindows)

Good Luck

---

### Post by l4zy on 2010-03-22
You are propably missing ntfs package from your ubuntu.

You have two optione either install ntfs-config
apt-get install ntfs-config and use gksu ntfs-config command 

or

install ntfs-3g with apt-get and mount you drivers manually if they aren't mounted automatically.

fdisk -l will tell you which driver has you win* things.

---

### Post by gordintoronto on 2010-03-22
If you are using a current version of Ubuntu, you should be able to click on Places/computer, and the other partition(s) should be visible. On my system there is a line which says "62.8 GB Media" which is actually my Windows 7 partition.

The previous "answers" you received only apply to older versions of Ubuntu.

---

### Post by tooler on 2010-03-23
thanks very much
worked fine

---

