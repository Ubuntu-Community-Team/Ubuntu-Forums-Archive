---
title: "formatting the system."
date: 2010-01-10
forum: General Help
---

### Post by harivittal.hk on 2010-01-10
hello friends,

I have got 2 OS in my desktop ie winXP n LINUX,will use both of them..

but ma system has become terribly slow,m not able to run any high-end apps for long duration,its not compatible so should format the entire system now,hav 512MB RAM n 160GB HD,m using 30GB for LINUX.
I request u ppl to PLEASE help me out by giving me best n suitable guidelines in achieving the same..
thank u.:)

---

### Post by akand074 on 2010-01-10
If your booted into either XP or Linux one should not effect the other in the sense of usage. Meaning your inability to run high-end apps for a long duration isn't because you are dual booting, from what I see its probably your hardware, I'd suggest getting more RAM. Anyways if you only wanted to go back to one OS you could use a recovery disk/partition or windows XP disk to reformat your drive and stick to windows or if you wanted just Linux you could use the ubuntu cd to do everything. Though like I said I don't think you'll get any better performance from removing an OS. Your windows partition is probably just clogged up with stuff I'd reformat that partition using a recovery disk or windows XP cd. Your ubuntu partition should be running the best it can using your hardware.

---

### Post by harivittal.hk on 2010-01-10
> **akand074 said:**
> If your booted into either XP or Linux one should not effect the other in the sense of usage. Meaning your inability to run high-end apps for a long duration isn't because you are dual booting, from what I see its probably your hardware, I'd suggest getting more RAM. Anyways if you only wanted to go back to one OS you could use a recovery disk/partition or windows XP disk to reformat your drive and stick to windows or if you wanted just Linux you could use the ubuntu cd to do everything. Though like I said I don't think you'll get any better performance from removing an OS. Your windows partition is probably just clogged up with stuff I'd reformat that partition using a recovery disk or windows XP cd. Your ubuntu partition should be running the best it can using your hardware.

yeah thanks for d rply...

dual booting has nothin much to do with the performance,tats true, but the thing is i want to know can i just reformat ma winXP part without disturbing LINUX n if i want to allocate more HD space for LINUX,how can i do tat, is GParted the only way??
thanku again..:)

---

### Post by adam814 on 2010-01-10
Sure, you should be able to re-format your Windows partition without bothering your Linux one(s) provided you're careful about it (just make sure in the Windows installer you only install in your NTFS-formatted Windows partition, not free space or anything like that).

I wouldn't say GParted is the only way to make more space for Linux, but in my opinion it's one of the better ways.  There are always the command line Linux utilities (fdisk, resize2fs, ntfsresize, etc.).  Or you could use 3rd-party Windows software like Partition Magic (don't know if they fully support ext4 though) to do it.

I prefer GParted as it's an intuitive GUI, it supports all common filesystems, and I like and understand the GPL license a lot better than the licenses for most Windows software.  EULA is a four-letter word after all.

---

### Post by stomakmonkee on 2010-01-10
Gparted is not the only way, but Gparted is the easiest way.  You can format your partition using whatever file system you want, and resizing the partition is all graphical, as you can just drag an arrow one way or the other.

---

