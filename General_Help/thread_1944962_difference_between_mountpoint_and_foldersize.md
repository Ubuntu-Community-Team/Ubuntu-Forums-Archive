---
title: "difference between mountpoint and foldersize"
date: 2012-03-22
forum: General Help
---

### Post by vinterkind on 2012-03-22
Hi all,

I did not know where to put it, so it's here. :-)

I've a harddisk with a size of 120 Gigabytes. It is mounted locally at /local.

df output is somewhat this:
```
/dev/sdb1    btrfs    120G  112G  5.3G  96% /local
```

and the folder itself (with du)
```
89G    local/
```

As you can see, the filesystem is btrfs (I tried it for the first time there). Any suggestions why there is so much of a difference in available space ? About 20 gigs of FS overhead seems to me too much. :confused:

No hidden folders inside. (That's why I've invoked du for the main folder.)
System is Ubuntu 11.10 x64

cheers,

---

### Post by Habitual on 2012-03-22
```
df -h 
```
output please.

---

### Post by vinterkind on 2012-03-22
> **Habitual said:**
> ```
df -h 
```output please.

Erm, I thought you just need the already posted line. But fine ...

```
# df -h -T
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda3     ext4    103G   13G   85G  13% /
udev      devtmpfs    7.9G  4.0K  7.9G   1% /dev
tmpfs        tmpfs    3.2G  864K  3.2G   1% /run
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    7.9G  1.4M  7.9G   1% /run/shm
/dev/sda1     ext4    230M   50M  168M  23% /boot
/dev/sdb1    btrfs    120G  112G  5.0G  96% /local
```

So there's nothing new ... 

I understand that btrfs has a lot of overhead, but the only thing i can see is this

```
# btrfs filesystem df /local
Data: total=109.75GB, used=109.49GB
System, DUP: total=16.00MB, used=24.00KB
System: total=4.00MB, used=0.00
Metadata, DUP: total=2.38GB, used=883.38MB
```

So only 2 Gigs of Metadata ...

It seems I have no snapshots or else

```

# btrfs subvolume list /local

```

---

### Post by Habitual on 2012-03-22
ya, I brain-farted, sorry.

---

### Post by ssam on 2012-03-24
free space in btrfs is handled very differently from in other filesystems. So far there seems to be no plan to make df give more sensible output.

did you read
[http://btrfs.ipv5.de/index.php?title=FAQ#Why_are_there_so_many_ways_to_check_the_amount_of_free_space.3F](http://btrfs.ipv5.de/index.php?title=FAQ#Why_are_there_so_many_ways_to_check_the_amount_of_free_space.3F)

ps:
there have been a lot of important bug fixes in btrfs in kernels 3.1, 3.2 and 3.3. if you are still using the 3.0 kernel in ubuntu 11.10 then you might want to think about getting a newer kernel from the ubuntu mainline kernel ppa, or upgrading to the 12.04 beta (which has 3.2).

---

### Post by vinterkind on 2012-04-02
> **ssam said:**
> free space in btrfs is handled very differently from in other filesystems. So far there seems to be no plan to make df give more sensible output.

did you read
[http://btrfs.ipv5.de/index.php?title=FAQ#Why_are_there_so_many_ways_to_check_the_amount_of_free_space.3F](http://btrfs.ipv5.de/index.php?title=FAQ#Why_are_there_so_many_ways_to_check_the_amount_of_free_space.3F)

ps:
there have been a lot of important bug fixes in btrfs in kernels 3.1, 3.2 and 3.3. if you are still using the 3.0 kernel in ubuntu 11.10 then you might want to think about getting a newer kernel from the ubuntu mainline kernel ppa, or upgrading to the 12.04 beta (which has 3.2).

Yep. Thank you so far. I've checked the document - but I suppose that I'll move to another filesystem. It's like 20Gigs of Overhead (through storing my data inappropriate) and I may check it again in some months then. 

I'll read them documents more carefully later - but for now I close that thread solved.

---

