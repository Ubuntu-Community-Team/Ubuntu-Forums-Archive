---
title: "File rights problem? Disc behaves as full but isn't."
date: 2009-09-19
forum: General Help
---

### Post by dumpsterdiver on 2009-09-19
Hi,

My Ubuntu setup has been working without problem since maybe a year. After the summer when I started up my system and had installed all updates the following problem occured:

I have one disc for root and home that seems to work well as usual. The problem is on the other disc, a 500 GB disc I use for music.
[B]
When I try to write something to the disc Nautilus says it is full.

[/B]_**With df (see below):**_Looks full, and it seems to have a maximum capacity of 459 GB.[U][B]
In sudo Nautilus:[/B][/U]17 674 objects, with total 220,1 GB. This is also about the size of the files on it to my knowledge.

_**When I remove 32 GB of files from the drive:**_ In Nautilus, free space is 32 GB and I can put stuff back in those 32 GB, but not more.
[B]
I guess this is a problem with the file rights, but I don't know where to start.[/B] :confused:
**Help would be so very appreciated!**



[B][SIZE=2]What I've tried so far[/SIZE]
[/B]Cleaned up *fstab*.
Runned *fsck* on it at startup (seems ok).

** [SIZE=2]My system info[/SIZE]**
Ubuntu 9.04 - Jaunty Jackalope

a@deluxe:~$ df -h
Filsystem            Storlek Anvnt Tillg Anv% Monterat på
/dev/sdb1              19G  4,1G   14G  24% /
tmpfs                 991M     0  991M   0% /lib/init/rw
varrun                991M  316K  991M   1% /var/run
varlock               991M     0  991M   0% /var/lock
udev                  991M  152K  991M   1% /dev
tmpfs                 991M  1,7M  990M   1% /dev/shm
lrm                   991M  2,2M  989M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdb3             164G   25G  131G  16% /home
/dev/sda1             459G  449G     0 100% /mnt/violen

---

### Post by yabbadabbadont on 2009-09-19
By default, whenever an ext2/ext3 filesystem is created, 5% is reserved for the root user.  If it is an ext3 filesystem, then some of the space is used by the journal.  But it generally doesn't use much space.  Also, be sure that you don't confuse the drive manufacturer's GB for the GiB that is generally used in Linux.  (GB = 1000, Gib = 1024)

Edit: an example of what I mean is in order.

GB:  500*1000^3 = 500,000,000,000
GiB: 500*1024^3 = 536,870,912,000

---

### Post by dumpsterdiver on 2009-09-19
Thanks for you answer!

Yes, in my post I'm mixing GB GiB, sorry for that, but this doesn't explain what is messed up ..

Also I can't see that it would be the 5% that is the problem, since it is more than half of the drive that is unavailable.

What is it with the file rights that could behave like this, making free space on the drive "reserved" in some way? Or is it not in the rights maybe? Should I check something else?

---

### Post by yabbadabbadont on 2009-09-19
How do you get that half is missing since:
> /dev/sda1 **459G 449G** 0 100% /mnt/violen

Edit: Also, it will show as full if you run out of inodes just as if you had used all the space.  "df -i" will show inode usage.

---

### Post by 73ckn797 on 2009-09-19
> **dumpsterdiver said:**
> Should I check something else?

See whether trash is empty. I had the same basic issue a while back but cannot find that info right away. There was a trash issue where the deleted files were not being completely deleted.

I will get back. Google for the answer, you will probably find it in the forums.

---

### Post by dumpsterdiver on 2009-09-19
> **yabbadabbadont said:**
> How do you get that half is missing since:


Yes, that is just why I don't get it. With *df* it looks just as it should (if the drive had about 450 GiB of files on it), **but** in *gksudo nautilus* it says a total of 188,5 GB of files and 18,7 GB free. Which would mean it only has a capacity of about 200 GiB. That just can't be right with a 500 GB disc that has a partition that should cover the whole disc? Can it? Even if I mixed GB and GiB just as well ... :)

---

### Post by dumpsterdiver on 2009-09-19
> **yabbadabbadont said:**
> Edit: Also, it will show as full if you run out of inodes just as if you had used all the space.  "df -i" will show inode usage.r

[FONT=Courier New]a@deluxe:~$ df -i -h
Filsystem            Inoder IAnvända  IFria IAnv% Monterat på
/dev/sdb1               1,2M    167K    1,1M   14% /
tmpfs                   213K       3    213K    1% /lib/init/rw
varrun                  213K      67    213K    1% /var/run
varlock                 213K       2    213K    1% /var/lock
udev                    213K    1,6K    211K    1% /dev
tmpfs                   213K       2    213K    1% /dev/shm
lrm                     213K      17    213K    1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdb3                11M     31K     11M    1% /home
/dev/sda1                30M     24K     30M    1% /mnt/violen

**[FONT=Arial]This looks ok I guess?[/FONT]**
[/FONT]

---

### Post by gadolinio on 2009-09-19
Mmm have you opened gparted partition editor to see what it says about the unit's status?

---

### Post by yabbadabbadont on 2009-09-19
> **dumpsterdiver said:**
> Yes, that is just why I don't get it. With *df* it looks just as it should (if the drive had about 450 GiB of files on it), **but** in *gksudo nautilus* it says a total of 188,5 GB of files and 18,7 GB free. Which would mean it only has a capacity of about 200 GiB. That just can't be right with a 500 GB disc that has a partition that should cover the whole disc? Can it? Even if I mixed GB and GiB just as well ... :)

Ahh, I missed that originally.  You are correct, that doesn't make any sense...

> **dumpsterdiver said:**
> r

[FONT=Courier New]a@deluxe:~$ df -i -h
Filsystem            Inoder IAnvända  IFria IAnv% Monterat på
/dev/sdb1               1,2M    167K    1,1M   14% /
tmpfs                   213K       3    213K    1% /lib/init/rw
varrun                  213K      67    213K    1% /var/run
varlock                 213K       2    213K    1% /var/lock
udev                    213K    1,6K    211K    1% /dev
tmpfs                   213K       2    213K    1% /dev/shm
lrm                     213K      17    213K    1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdb3                11M     31K     11M    1% /home
/dev/sda1                30M     24K     30M    1% /mnt/violen

**[FONT=Arial]This looks ok I guess?[/FONT]**
[/FONT]

Yes, that looks fine too.  Weird.

What is the output of "sudo dumpe2fs -h /dev/sda1"?  (that just reads from the drive, it doesn't change it in any way)

EDIT: Also, have you checked the Trash for that drive as suggested by a previous poster?

---

### Post by dumpsterdiver on 2009-09-19
Ok, it goes like this:

When I run *sudo baobab* I **can** see that there is a trash called *.Trash-0* with the noble size of 228 GB!

There is also a trash called *.Trash-1000* that is empty.

The reason that I didn't find this was that I didn't run *baobab* in *sudo* from the beginning ... ](*,)

**What can have caused this and how do I aviod it in the future?**

---

### Post by yabbadabbadont on 2009-09-19
In Nautilus, there is a setting you can enable that enables a command to bypass the Trash when deleting things.  You can also highlight things and then use Shift-Delete to bypass the Trash.

(or you could just use the rm command in a terminal and not worry about the Trash at all ;))

((It won't ask any questions though, and once you use it, your files/directories will definitely be gone))

---

### Post by drs305 on 2009-09-19
> **dumpsterdiver said:**
> Ok, it goes like this:

When I run *sudo baobab* I **can** see that there is a trash called *.Trash-0* with the noble size of 228 GB!

There is also a trash called *.Trash-1000* that is empty.

The reason that I didn't find this was that I didn't run *baobab* in *sudo* from the beginning ... ](*,)

**What can have caused this and how do I aviod it in the future?**

These trash files are identified by the user ID. Trash-1000 belongs to the first user (uid=1000). The Trash-0 folder most likely belongs to root. You avoid this by using SHIFT-DEL when logged in as root in Nautilus and deleting a file. Be careful, as this command is not reversible. Or,as yabbadabbadont suggested, add the option to Nautilus to bypass the trash.

By the way, here is a link to a post I made about finding what is taking up space on your drives:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by dumpsterdiver on 2009-09-19
Yes, but no but, no but yes but :):

Thanks for the info, but my question (better formulated) is:
[B]
How come there was two trashes, one of wich I couldn't empty with the empty trash command?[/B]

---

### Post by drs305 on 2009-09-19
> **dumpsterdiver said:**
> Yes, but no but, no but yes but :):

Thanks for the info, but my question (better formulated) is:
[B]
How come there was two trashes, one of wich I couldn't empty with the empty trash command?[/B]

We had simultaneous posts, but I believe I answered above. This happens on non-linux file systems which aren't incorporated into the standard linux trash system.

---

### Post by yabbadabbadont on 2009-09-19
> These trash files are identified by the user ID. Trash-1000 belongs to the first user (uid=1000). The Trash-0 folder most likely belongs to root.

Your user's trash was empty, root's was not.  Until you ran the program as root, you did not have permission to see, let alone delete, the files.

---

### Post by dumpsterdiver on 2009-09-19
> **drs305 said:**
> These trash files are identified by the user ID. Trash-1000 belongs to the first user (uid=1000).

**Thanks you so very much everyone!!** This as exactly the info I was looking for and now I now what happend:

When I have to clear my backups (that are made with *Simple backup*) I have to use sudo. When I did that the root-trash was filled with garbage ... and I didn't know about this with separate trashes for every user (but of course it has to be like this). The result was that I didn't empty the trash.


/ Over and out from Sweden. Now I can work again!

---

