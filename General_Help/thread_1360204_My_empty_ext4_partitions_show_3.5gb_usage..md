---
title: "My empty ext4 partitions show 3.5gb usage."
date: 2009-12-20
forum: General Help
---

### Post by cormano on 2009-12-20
I have a 1tb drive. 
I created several ext4 partitions as shown in the pic:
[ATTACH]140668[/ATTACH]


204GB partitions(/media/storage1 and /media/storage2) show 3.5Gb usage. They are empty, no hidden folders no trash no root stuff, whatsoever.

/media/reserva is empty too, and yet it shows 765mb usage.
This seems to follow some kind of percentage rule. 
I already used tune2fs -m 0 on all the partitions.
So wheres the missing space, i wonder? I should have roughtly 930 gb, yet i only have 915, which more or less means im losing around 4gb per 250gb chunk. Is this the cost of journaling or something?

---

### Post by Leppie on 2009-12-20
> **cormano said:**
> /media/reserva is empty too, and yet it shows 765mb usage.
This seems to follow some kind of percentage rule. 
I already used tune2fs -m 0 on all the partitions.
So wheres the missing space, i wonder? I should have roughtly 930 gb, yet i only have 915, which more or less means im losing around 4gb per 250gb chunk. Is this the cost of journaling or something?

yes, this apparently is the journaling effect. i read somewhere on this forum it was about 5%, but you're indicating much less.

---

### Post by SecretCode on 2009-12-20
It's probably the "root reserved" allocation built into ext4 (and ext3 and I assume ext2). I think it's 5%, but oddly I can't find a reference.

It should probably scale to a smaller percentage for larger volumes but I don't know if this is being considered.

---

### Post by vaiocomputer on 2009-12-20
You should do a search for this or something like this, since I remember reading about a guy who had a similar problem.  It is because ext3 and ext4 saves a certain percentage of the hard drive for some reason, which becomes excessive in large hard drives, but if you do something that involves terminal, you can decrease the space specifically alloted for this.

---

### Post by SecretCode on 2009-12-20
> **Leppie said:**
> this apparently is ...
i read somewhere ...

> **SecretCode said:**
> It's probably ...
I think it's ...

> **vaiocomputer said:**
> I remember reading about ...
... for some reason ...
but if you do something that involves terminal ...

Well there you have it. A definitive and unambiguous answer. :P

---

### Post by cormano on 2009-12-20
If you are talking about the % of blocks reserved for the root, i already did that :(

tune2fs -m 0 on all the partitions.

---

### Post by SecretCode on 2009-12-20
Ah :(

Apart from gparted, do system commands also show nothing on the partitions? sudo ls -a, sudo df, sudo du?

---

### Post by cormano on 2009-12-20
sudo ls -a on /media/storage 3:

jherraez@GoldenSun:/media/storage3$ sudo ls -a
.  ..  lost+found

jherraez@GoldenSun:/media/storage3$ sudo du
16	./lost+found
20	.


Nothing there.


jherraez@GoldenSun:/media/storage3$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              46G  5.0G   41G  11% /
udev                 1007M  316K 1007M   1% /dev
none                 1007M  304K 1007M   1% /dev/shm
none                 1007M   84K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda4              36G  176M   36G   1% /media/reserva
/dev/sda2             202G  188M  202G   1% /media/storage3
/dev/sda3             230G   65G  165G  29% /media/storage4
/dev/sda7             202G  188G   15G  93% /media/storage1
/dev/sda8             202G  188M  202G   1% /media/storage2

Here it only says that my partitions are 202 GB, but im pretty sure they are nearly 205gb

---

### Post by cormano on 2009-12-20
Another way to put this.
BaoBab says the total filesystem space is 916 GB. A 1tb drive should have +-930 GB.

---

### Post by FearfulJesuit on 2009-12-20
So to add to more of the ambiguous/definitive answer provided by other people, I think that the 3.5 GB reserved spaces are used as swap spaces. So some of the process load can be transferred to the swap if needed. Do you have an OS installed on the other partitions? If so, then that is the swap space on that partition. If not, then I don't know what to tell you.

---

### Post by cormano on 2009-12-20
No other OS. i only have a 1gb partition for swap(956mb actually)

---

### Post by SecretCode on 2009-12-21
Time for more serious tools then. Try disktype & testdisk. Boot a live CD like PartedMagic and see if parted/gparted say the same things from there. Mount the dubious partitions and examine them from the live CD. Run e2fsck. 

If that fails, get the drive exorcised.

---

### Post by larstobi on 2010-05-01
> **cormano said:**
> I have a 1tb drive. 
I created several ext4 partitions as shown in the pic:

204GB partitions(/media/storage1 and /media/storage2) show 3.5Gb usage. They are empty, no hidden folders no trash no root stuff, whatsoever.

I just had these exact symptoms on a ext4 filesystem created by Ubuntu Lucid beta2. fsck reported the filesystem as "clean". I figured it had to be wrong, so I forced a check with "fsck -v -y -f /dev/md2", and indeed it found errors, basically five errors with wrong inode numbers. It fixed them and put the directories in lost+found, where I could manually move them in their proper places. Now everything is working fine again. I think it might be a bug, but I haven't been able to reproduce it.

---

### Post by dino99 on 2010-05-01
> **larstobi said:**
> I just had these exact symptoms on a ext4 filesystem created by Ubuntu Lucid beta2. fsck reported the filesystem as "clean". I figured it had to be wrong, so I forced a check with "fsck -v -y -f /dev/md2", and indeed it found errors, basically five errors with wrong inode numbers. It fixed them and put the directories in lost+found, where I could manually move them in their proper places. Now everything is working fine again. I think it might be a bug, but I haven't been able to reproduce it.

thats why you have to take care formatting tools, they can be bugged too and then built serious issues: google about your tools before using them  :P

---

