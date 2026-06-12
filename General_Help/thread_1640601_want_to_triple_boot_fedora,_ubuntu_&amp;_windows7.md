---
title: "want to triple boot fedora, ubuntu &amp; windows7"
date: 2010-12-08
forum: General Help
---

### Post by rockager on 2010-12-08
hi!! i have a 75gb hardisk with the windows installation taking 16gb and the rest (59gb) is unallocated.
i want to triple boot ubuntu, fedora & windows7 so that i can choose between them after booting.
how do i do it?

---

### Post by sikander3786 on 2010-12-08
You basically need at least 3 partition for both Fedora and Ubuntu.

1. Fedora System partition.

2. Ubuntu System partition.

2. Swap partition (Both OS can use the same).

The size of those partitions is up to you. I would suggest at least 10 GB for each System Partitions and RAM x 2 for Swap partition.

Install Fedora and at last install Ubuntu. That way you won't need to worry about Triple-Booting. Ubuntu's Grub should detect both Windows and Fedora and add it to Grub menu.

I assume there is only one primary partition there that hold Windows. Create an Extended and then 3 logical partitions inside it (Linux doesn't need a primary partition to boot from).

You can also create an additional Logical NTFS partition to share data between 3 of your OS.

You can also have a separate /home partition for Fedora or Ubuntu or both. But your disc space might count there.

---

### Post by rockager on 2010-12-08
why are secondary partitions needed anyway?
why can't i just make a primary partition for everything?

---

### Post by sikander3786 on 2010-12-08
> **rockager said:**
> why are secondary partitions needed anyway?
why can't i just make a primary partition for everything?
4 primary partitions is the limit (remember, extended partition itself is a primary partition and it counts there). If you eventually create more than that, you might be in a bit of trouble as it is reported that Windows automatically starts reading them as Dynamic Discs and Linux doesn't recognize Dynamic one's as it is a Microsoft proprietary thing ;-)

You can create as many Logical partitions as you wish.

---

### Post by rockager on 2010-12-08
thanks for telling me that.
would there be any problem while triple booting if i install both the linux distros on extended partitions?

---

### Post by sikander3786 on 2010-12-08
> **rockager said:**
> thanks for telling me that.
would there be any problem while triple booting if i install both the linux distros on extended partitions?
There shouldn't be any problems at all.

---

### Post by rockager on 2010-12-08
well then, this is my plan for partitioning:
primary partition1(windows)---------16gb
secondary partition:
           partition1(fedora)-------------15gb
           partition2(ubuntu)-------------15gb
           partition3(swap)---------------1gb
           partition4(data)----------------28gb
will it work?

---

### Post by sikander3786 on 2010-12-08
Surely. That partitioning scheme sounds good.

---

### Post by rockager on 2010-12-08
thanks very much, sikander. i appreciate your help.
wouldn't have been able to do it without your help. 
[U]
[/U]

---

### Post by v3nk! on 2011-01-12
Thanks a Lot buddy... was just looking for this.your description was extactly the kind I was looking. :)

---

