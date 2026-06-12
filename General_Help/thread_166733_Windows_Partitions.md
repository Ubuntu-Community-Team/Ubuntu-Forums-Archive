---
title: "Windows Partitions"
date: 2006-04-27
forum: General Help
---

### Post by Sonic5688 on 2006-04-27
I have a second hard drive in my pc (its actually my primary) running windows. Is there a way to make the files on that hard drive accessible through Ubuntu?

---

### Post by Sef on 2006-04-27
> I have a second hard drive in my pc (its actually my primary) running windows. Is there a way to make the files on that hard drive accessible through Ubuntu?

Yes, you need to create either a FAT32 or an ext2 partition.   Both Windows and Linux/GNU can read and write to both.

---

### Post by Sonic5688 on 2006-04-27
How do you go about doing that? you wont lose any data will you?

---

### Post by Sef on 2006-04-27
> How do you go about doing that? you wont lose any data will you?

If you have some free space on your disk, no you won't lose anything.  Use the live cd and then open GParted.  Applications > System Tools > GParted.

Just create a FAT32 or ext2 partition.

You won't lose any data this way.  However, **back up** your data first.  Things can always happen unfortunately.

---

### Post by wh0rd on 2006-04-27
If it's Windows XP it's most likely NTFS if its not and is FAT32 then you can edited in Ubuntu. Here is a guide to help you get connected to that hard drive:
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by Sonic5688 on 2006-04-27
Thanks alot guys! Now I wont have to switch between hard drives anymore!

---

