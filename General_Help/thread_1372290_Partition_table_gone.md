---
title: "Partition table gone"
date: 2010-01-04
forum: General Help
---

### Post by stuart.reinke on 2010-01-04
Hi and happy new year everyone. 
I seem to have lost the partition table on my hard drive. From what i've been able to learn from googleing the problem, it happened when I resized /sda1 and installed windows on the unallocated space. It appears that my hard drive is now being writen to as if it were a large floppy. All data is in tact. 
Is there any way to fix this or is my only option to back up /home and reinstall. By the way, g-parted reads the disk as completly unallocated.
Thanks for any advice you might have.
Stu

---

### Post by rbc on 2010-01-04
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by sylvester_0 on 2010-01-04
> **rbc said:**
> [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
+1! That program saved my bacon when playing around with different bootloaders on my Hackintosh. It's in the repos! :guitar:

---

### Post by stuart.reinke on 2010-01-04
> **rbc said:**
> [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Thanks. I'll give a try.

---

### Post by Joe Ker1086 on 2010-01-04
good luck, test disk is awsome but i had the same problem and it kept finding a gpt partition and could not restore my fedora partition. you might wanna try [this]("http://gag.sourceforge.net/") if it doesnt work. I would start with testdisk but i have heard very good things about GAG and everyone ive talked to that used it has said it found their partitions with no problem.

---

### Post by stuart.reinke on 2010-01-04
> **sylvester_0 said:**
> +1! That program saved my bacon when playing around with different bootloaders on my Hackintosh. It's in the repos! :guitar:

Can it be run on a mounted drive?
Will it work on ext4?

---

### Post by stuart.reinke on 2010-01-04
@ Joe Kerr1086
Thanks for providing a plan "B" :)

---

### Post by Joe Ker1086 on 2010-01-04
I have never run it on a mounted drive before, sorry, and per the wiki it does not specifically say it works with ext4....  [TestDisk Wiki]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by stuart.reinke on 2010-01-04
> **Joe Ker1086 said:**
> I have never run it on a mounted drive before, sorry, and per the wiki it does not specifically say it works with ext4....  [TestDisk Wiki]("http://www.cgsecurity.org/wiki/TestDisk")

I noticed the absence of ext4 on the list, that's why I asked.
All I can do is give it a try I guess.

---

### Post by OldGrantonian on 2010-01-05
> **stuart.reinke said:**
>  
I seem to have lost the partition table on my hard drive.

As a newbie, I try to keep my head down. But I would be most grateful, for my own experience, if you could tell me how you know that your partition table is "lost".
.

---

### Post by OldGrantonian on 2010-01-05
> **OldGrantonian said:**
> As a newbie, I try to keep my head down. But I would be most grateful, for my own experience, if you could tell me how you know that your partition table is "lost".
.

Bump :)

---

### Post by OldGrantonian on 2010-01-06
Bump :)
.

---

### Post by OldGrantonian on 2010-01-09
Bump :)

---

### Post by ibuclaw on 2010-01-09
Usually listing the partition table helps.
```
sudo fdisk -l
```
If that brings up nothing - or errors, you **may** be in trouble. :)

If you have any further queries, please start your own thread.

Regards
Iain

---

