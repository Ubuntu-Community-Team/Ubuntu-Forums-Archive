---
title: "Hard drive space missing?"
date: 2010-07-09
forum: General Help
---

### Post by draigars on 2010-07-09
Hello,

I have a 320 GB hard drive, which means 303,85 GiB (thanks GParted!). Partitioned this way:
/dev/sda1 (ext4) = 292.33 GiB
/dev/sda2 (extended) = 5.76 GiB
       /dev/sda5 (linux-swap) = 5.76 GiB (inside /dev/sda2)

But... there is a problem. According to Baobab 2.30.0 (a graphical tool to analyze disk usage), I have **287.7 GiB** (compared with 292.33 GiB, this is not a big difference) disk space: 171 GiB used, and 116.7 GiB free.

The problem is: the only folder which appears in the first level is "/" (obviously)... and use only 98.7 GiB ([here is a screenshot]("http://img822.imageshack.us/img822/1707/bamboo.png"), in french, but well... easy to understand; Gio = GiB).

In Nautilus also, when on /, Right Click > Properties shows about 90 GiB used space.

So... where have the other (~70 GiB) used disk space gone?

**df**:
```
draigars@draigars-desktop:~$ df
Files sys.        1K-blocks         Occuped       Available    Capacity        Mounted on
/dev/sda1         301717936       179356440       107035088         63%                 /
none                1026596             300         1026296          1%              /dev
none                1030816             324         1030492          1%          /dev/shm
none                1030816             200         1030616          1%          /var/run
none                1030816               0         1030816          0%         /var/lock
none                1030816               0         1030816          0%      /lib/init/rw

```**sudo fdisk -l**:
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk ID : 0x6148c5f4

Device          Bait      Start       End        Blocks      Id                  System
/dev/sda1          *          1     38161     306528201      83                   Linux
/dev/sda2                 38162     38913       6040440       5                Extended
/dev/sda5                 38162     38913       6040408+     82    Linux swap / Solaris

```Hope you can help!

Thanks.

---

### Post by matey3 on 2010-07-09
this is a common problem.I think?

you see 1 kilobyte is really 1024 bytes.
they say Kilo (1000) but in reality since everything in computers is 2 to the power of some number (here,  2 ^ 10 = 1024).

This 24 extra bytes adds up when you deal with great numbers like 90 GB which is 90, thousand, million bytes.

Some systems add the 24 bytes some dont and some estimate.
I hope that is what your question was?

---

### Post by audiomick on 2010-07-09
Apart from what matey3 wrote, the file system itself has an overhead that it needs for administration purposes. I believe this is 5% on a standard Ubuntu system, so if the drive is large, it can be a fair bit that just "disappears". The value can be adjusted, but I don't know how to do it.

---

### Post by draigars on 2010-07-09
Thanks for the quick answer!

Well, damn nano, it seems that a part of my post was gone, so it's pretty nonsense... Sorry.

Yes, I know there is a difference between GB and GiB (base ten, base two), and thus a difference can appears...

Initial message edited, and there is a screen that makes things clearer:
[IMG][IMG]file:///tmp/moz-screenshot.png[/IMG]http://img215.imageshack.us/img215/4965/bamboo2.png[/IMG]

Translation: > Total system capacity: **288.7 GiB** (**used: 171.0 GiB**; free: 116.7 GiB)And then:
> Folder "/", **size: 98.7 GiB**So... my only root folder (/) uses **98.7 GiB**, but it says **171 GiB** is used in total.

Where are the other ~70 GiB gone?

Thanks, and sorry for the nonsense and my poor english. :-*

EDIT:
@[audiomick]("http://ubuntuforums.org/member.php?u=553389"): Yes, I know, I think it's normal that I loose 11.52 GiB (3.8% of total space) for system administration purpose. But ~71 GiB (about 25% of my whole hard drive) is a lot. Thanks though. :)

---

### Post by NFblaze on 2010-07-09
Try running the File Disk Analyzer as a root user.

Also, try using* sudo df -h*, in the terminal.

---

### Post by draigars on 2010-07-09
I posted a df (without -h though) on the first message, here is the sudo df -h:
```
Sys. de fich.         Size     Occ.      Disp.     %Occ.         Monté sur
/dev/sda1             288G      174G      100G        64%                /
none                 1003M      300K     1003M      1%              /dev
none                 1007M      688K     1006M      1%           /dev/shm
none                 1007M      200K     1007M      1%        /var/run
none                 1007M         0     1007M      0%       /var/lock
none                 1007M         0     1007M      0%    /lib/init/rw

```About the File Disk Analyzer, the only thing I have is the Disk Utility (system > administration). Do you mean this?

Oops, forgot to mention, I'm using 10.04, Gnome.

---

### Post by NFblaze on 2010-07-10
Yea, I dont think File Disk Analyzer has full access rights to the entire system. It usually gives me two different outputs depending on whether I run it as a regular user or if I use sudo baobab as a root user. Check both.

---

### Post by draigars on 2010-07-10
Well, I found the source of the problem: the content of some huge folders (mainly Videos) was hidden (even as root user) though I could access to these folders (some strange rights). Apparently, the complete delete of wine has caused it.

And about sudo baobad, it shows me that "/" use 33 GiB...

Everything is back now, problem solved, just had to change the rights.

Thanks a lot for your help!

---

