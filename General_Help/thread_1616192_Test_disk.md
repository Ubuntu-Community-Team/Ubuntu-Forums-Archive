---
title: "Test disk?"
date: 2010-11-07
forum: General Help
---

### Post by jotacebusta on 2010-11-07
Hi all,

I have a dell inspiron 1420, with a 80 Gb disk. This is partitioned in two partition. One is 10 Gb, in which I have unbuntu 10.04, and the other is where I have all my data, whoch mounts in /mnt/data

The system tells me that I'm lacking of space, but this is very weird: I have a litle bit more than 25Gb of data. Gparted sees the partition ad tells I have a lot of free place. But the disk use tool ("analizador de uso de disco" in spahish) says that  mnt is used to 67%, and the files size is 16.7Gb.  

Is it possible that my hard disk is somehow dammaged? What should I do to know?

Thanks

JC

---

### Post by jotacebusta on 2010-11-07
I forgot to saye: something still stranger: when I right-click on my home/myuser folder, and I ask for properties, the computer says that I have 37.1Gb of free space, and only 5.3Gb of data

But It happens that in that precise folder I have a .Virtualbox folder which contains a tiny xp virtual machine, with 10Gb of hard disk.

I'm really confused!

---

### Post by cipherboy_loc on 2010-11-07
What is the output of:
```
sudo fdisk -l
```
That will help us with the partitions. Also, I have noticed discrepancies between various disk usage counters (The default one in gnome, gdmap, conky's disk usage, etc). I cannot answer why, but I think it has to do with the differences between GB (1000MB, a MB being 1000KB, which is 1000B (which I think is 8 bits)) and a GiB (Which is 1024MiB, a MiB being 1024KiB, which is 1024B (which is 8 bits)). But that would not explain why everything gives you a different answer. 

If everything says that you have enough disk space, I would recommend just ignoring it. BTW, take a screen shot of the message when it pops up next. I would like to see what drive it is talking about (Which might give us some clues).



Cipherboy

---

