---
title: "says hard disk is almost full but shouldn't be!!!!"
date: 2012-07-13
forum: General Help
---

### Post by mrphud on 2012-07-13
Hi all,

I am looking at disk usage analyzer and it tells me that I am using only 93% of the 250 available, however, when I scan the file system only 20 GB are said to be used. Where is the other space. What is taking it? How to I get it back. I tried to use computer janitor, but there is nothing to clean up! 

Does anyone know why this is occuring?

---

### Post by Rsjc741 on 2012-07-13
My guess is imminent drive falure.
 
Probably data corruption.
 
Is it a SSD or a regular spinning disk?
 
How old?
 
Could be malware, but I doubt it

---

### Post by prshah on 2012-07-13
> **mrphud said:**
> I am looking at disk usage analyzer and it tells me that I am using only 93% of the 250 available, however, when I scan the file system only 20 GB are said to be used.

Many possibilities, we need more information to check:

a) Most likely: Your 250GB HDD is partitioned, and you are running out of space on a particular partition. 

b) You are running out of inodes. Have many thousands of small files (eg like cookies) can cause such a problem.

c) Scanning the file system as an unpriviledged user may not include some files / directories whose permissions are restricted.

Please check/post the output of the following from a terminal```
df -h
df -i
``` This will give us information that can help pinpoint a problem, if one exists.

---

### Post by The Linuxist on 2012-07-13
You can also see where the space is going by trying:

```
sudo du -h --max-depth=1 --exclude 'proc' /
```

this will take a moment to complete, but it gives you a good breakdown of the usage of different directories.

---

### Post by YfoMp5QBh2 on 2012-07-13
> **mrphud said:**
> Hi all,

I am looking at disk usage analyzer and it tells me that I am using only 93% of the 250 available, however, when I scan the file system only 20 GB are said to be used. Where is the other space. What is taking it? How to I get it back. I tried to use computer janitor, but there is nothing to clean up! 

Does anyone know why this is occuring?

Doesn't the disk usage analyser tell you what is taking up all the space? There is usually a pie chart and the column on the left should indicate what portion of the pie chart is taken up on the disk.

If that doesn't yield an obvious result I'd check your partitions as suggested.

---

### Post by mrphud on 2012-07-15
```
me@workerbee:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             221G  205G  4.4G  98% /
udev                  4.0G  4.0K  4.0G   1% /dev
tmpfs                 1.6G  816K  1.6G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  4.0G  120K  4.0G   1% /run/shm
/dev/sr0              3.1G  3.1G     0 100% /media/Data disc (15 Feb 12)
me@workerbee:~$ df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1            14655488  504204 14151284    4% /
udev                  195287     569  194718    1% /dev
tmpfs                 198794     487  198307    1% /run
none                  198794       1  198793    1% /run/lock
none                  198794       5  198789    1% /run/shm
/dev/sr0                   0       0       0    -  /media/Data disc (15 Feb 12 
```

here is the output to the df -ih

---

### Post by mrphud on 2012-07-15
below is the output for the du -h command. it looks like var takes most of the space. What is in there?

```
me@workerbee:~$ sudo du -h --max-depth=1 --exclude 'proc' /
180K	/tmp
8.1M	/sbin
4.0K	/cdrom
1.2G	/lib
192G	/var
4.0K	/mnt
4.0K	/selinux
84M	/opt
18M	/etc
200K	/srv
210M	/boot
0	/sys
8.4M	/bin
du: cannot access `/home/me/.gvfs': Permission denied
5.1G	/home
6.2G	/usr
4.0K	/dev
16K	/lost+found
3.1G	/media
936K	/run
812K	/root
208G	/

```

---

### Post by Elfy on 2012-07-15
I'd have a look at what you have in /var - specifically /var/log


> 192G	/var

> /dev/sda1 221G 205G 4.4G 98% /

AAs it says - you've 4.4G left on /

try the command in post #4

Have a look here [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by mrphud on 2012-07-15
The disk usage analyzer doesn't tell me where the bulk of the space is being used. But apparantly the above commands do. Probably because I need to be root.

---

### Post by Elfy on 2012-07-15
> sudo du -h --max-depth=1 /var

try that

---

### Post by mrphud on 2012-07-15
It appears to be in the backup. Can I just delete this folder? I doubt I need it. 

```
me@workerbee:~$ sudo du -h --max-depth=1 /var 
150M	/var/spool
1.2M	/var/tmp
191G	/var/backup
8.5M	/var/backups
20K	/var/games
4.0K	/var/mail
4.0K	/var/local
503M	/var/lib
370M	/var/cache
4.0K	/var/opt
4.0K	/var/crash
154M	/var/log
192G	/var

```

---

### Post by mrphud on 2012-07-15
It turns out it was storing a lot of info in the backup folder. I decided to use nautalis and delete the all but the most recent backup file. This should clear a lot of space.

---

