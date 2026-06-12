---
title: "ubuntu question"
date: 2006-06-16
forum: General Help
---

### Post by thunderfox933 on 2006-06-16
could i install ubuntu to anthor harddisk. like have 1 harddisk dedicated for microsuck crapdows xp. And the second harddisk decicated to ubuntu

---

### Post by rado_london on 2006-06-16
On theory you can but I cant say if it will be easy though.

---

### Post by aysiu on 2006-06-16
It can be done easily. You just have to know which partitions are which.

[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html) should help.

---

### Post by PBK on 2006-06-16
Yep - It's easy. Like Aysiu said, you just need to know where it's plugged in at on you computer. I did that until I was sure ubuntu was for me. I no longer have the second drive for ubuntu; Ubuntu is now on the main HD!

PK

---

### Post by maniacmusician on 2006-06-16
[QUOTE=aysiu]It can be done easily. You just have to know which partitions are which.

[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html) should help.[/QUOTE]


It didn't say anything about installing xubuntu to a second disk...I was sort of wondering about this too. If one drive is set as master and the other as slave, how can you put Ubuntu on the second (slave) drive? Does BIOS let you boot from slave drives?

---

### Post by aysiu on 2006-06-16
Yes, after you select to manually edit the partition table, you will get to a graphical summary of your partitions.

The screen *after* that summary allows you to have the second (slave) drive be mounted as / (it will probably be /dev/hdb1, but you should have a look to double-check).

---

### Post by maniacmusician on 2006-06-16
that seems to be tantamount to what this user wants...he doesnt want to partition his first drive, he wants to install ubuntu totally on his second drive. and if that drive doesn't  show up in the graphical summary (which is where, i'm pretty sure, you're supposed to create and allocate sizes for partitions), how is he going to do that?

---

### Post by Fred Doolie on 2006-06-16
[QUOTE=maniacmusician]how can you put Ubuntu on the second (slave) drive? Does BIOS let you boot from slave drives?[/QUOTE]

Just install it to hdb or however your second drive shows up in the partitoniing section.

Some Bios let you boot from slave drives but you don't have to.
Ubuntu will install the Grub bootloader on your main drive.
When you boot you will get a menu like

Ubuntu Linux Kernal K7 12-5-98  
Memory Test
Windows XP

and you can boot whatever you want.

---

### Post by Fred Doolie on 2006-06-16
[QUOTE=maniacmusician]he doesnt want to partition his first drive, he wants to install ubuntu totally on his second drive.[/QUOTE]

That's how mine is set up.  Win2000 on master and Ubuntu on slave. Ubuntu did it automagically.

---

### Post by aysiu on 2006-06-16
[QUOTE=maniacmusician]that seems to be tantamount to what this user wants...he doesnt want to partition his first drive, he wants to install ubuntu totally on his second drive. and if that drive doesn't  show up in the graphical summary (which is where, i'm pretty sure, you're supposed to create and allocate sizes for partitions), how is he going to do that?[/QUOTE]
If the drive doesn't show up in the graphical summary... well, that's another problem...

I'm talking about the way things are *supposed* to work.

---

### Post by maniacmusician on 2006-06-16
ah okay...thank goodness for grub then. i didn't realize it could do that...

---

