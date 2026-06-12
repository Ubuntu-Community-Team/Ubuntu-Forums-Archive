---
title: "remove partitions"
date: 2010-03-28
forum: General Help
---

### Post by andrew_a72 on 2010-03-28
Im running Ubuntu 9.10 dual boot with Windows XP, on my 120GB hard drive I currently have the following partitions

a) 42GB - with WindowsXP installed
b) 10GB - for WindowsXP storage
c) 3.1GB - accidentally made when installing Ubuntu
d) 62GB - With Ubuntu installed
e) 2.7GB - swap space for ubuntu

I very rarely use WinXP and have nothing on b or c, so my question is can I get rid of those partitions to make d 75GB total without having to reinstall Ubuntu?

Thanks in advance,

---

### Post by 2hot6ft2 on 2010-03-28
Post a screenshot of GParted
System > Administration > GParted
Applications > Accessories > Take Screenshot
Choose "Grab the current window" so it will be big enough to read
so we can see how it's layed out and if there are are any extended partitions.
Attach the screenshot
But no you shouldn't need to re-install.

---

### Post by Kevinator on 2010-03-28
Deleting partitions is easy, but that just turns them into unused space.

Resizing partitions to consume adjacent unused space is easy, too.

Resizing a **file system**, that I don't know about. It's theoretically possible, but I don't trust it. There's no way I would try it without having the data backed up first.

---

### Post by 2hot6ft2 on 2010-03-28
> **Kevinator said:**
> Deleting partitions is easy, but that just turns them into unused space.

Resizing partitions to consume adjacent unused space is easy, too.

Resizing a **file system**, that I don't know about. It's theoretically possible, but I don't trust it. There's no way I would try it without having the data backed up first.
It's not hard. Just need to know where everything is and it's done from the livecd and grub-pc is reinstalled so it matches the new configuration.
It's really not that bad but backups should always be done since things can go wrong.

---

### Post by john newbuntu on 2010-03-29
Food for thought:
1. Merge b and c to ext4 and move /home there from d (space permitting).  This way, future upgrades to Ubuntu on d are clean
2. Merge b and c to NTFS just for common storage since you use Win (rarely though)

---

### Post by andrew_a72 on 2010-04-05
I messed something else up so I finally ended up completely reinstalling Ubuntu. Took awhile but it works.


Thanks for the help anyway though

---

