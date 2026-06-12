---
title: "Hard Drive space"
date: 2009-06-28
forum: General Help
---

### Post by IceTerminal on 2009-06-28
I've done a search for my problem but could not find anything, so please forgive me if I've missed it.

My problem is that my drive is reporting that its 97% full. Doing some initial checks, I can't find any reason why it would say this as my drive is 250GB in size but only about 83GB is being used. 
I'm using 9.04 server 32bit.
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             229G  210G  7.6G  97% /
As you can see, its saying its almost full. But doing a check on what directories are using what, it only shows that 83% is being used.
# du -xhc --max-depth=1
6.1M    ./bin
186M    ./boot
700K    ./root
4.0K    ./downloads
0    ./sys
88K    ./tmp
4.0K    ./opt
4.0K    ./selinux
4.0K    ./srv
12K    ./media
0    ./proc
16K    ./lost+found
76G    ./files
556M    ./home
2.9G    ./usr
2.6G    ./var
1.5G    ./lib
16K    ./audio
20K    ./mnt
23M    ./etc
4.0K    ./initrd
0    ./dev
7.3M    ./sbin
83G    .
83G    total

Doing a manual check of du -h shows basically the same.
Directories within the / partition
/bin = 6.1M
/boot = 186M
/cdrom -> media/cdrom = 0
/dev = 312K
/etc = 23M
/files = 76G
/home = 556M
/initrd = 4.0K
/lib = 1.5G
lost+found = 0
/media = 12K
/mnt = 20K
/opt = 4.0K
/proc = 0  ???
/root = 700K
/sbin = 7.3M
/selinux = 4.0K
/srv = 4.0K
/sys = 0  
/tmp = 88K
/usr = 2.9G
/var = 2.6G

So I"m looking for help on this one. I"m not running anything weird, just a normal server running web, email, etc. Can someone point me in the right direction that can  help me find and clear this? Thank you very much in advance.

---

### Post by blueridgedog on 2009-06-28
Can you post the output of:

```
cd /
sudo du --max-depth=1 | sort -g
```

and

```
df
```

---

### Post by IceTerminal on 2009-06-29
Certainly
> du --max-depth=1 | sort -g
du: cannot access `./proc/8563/task/8563/fd/3': No such file or directory
du: cannot access `./proc/8563/task/8563/fdinfo/3': No such file or directory
du: cannot access `./proc/8563/fd/3': No such file or directory
du: cannot access `./proc/8563/fdinfo/3': No such file or directory
0    ./proc
0    ./sys
4    ./initrd
4    ./opt
4    ./selinux
4    ./srv
12    ./media
16    ./lost+found
20    ./mnt
276    ./tmp
312    ./dev
716    ./root
6176    ./bin
7384    ./sbin
23328    ./etc
189480    ./boot
577304    ./home
1474780    ./lib
2783212    ./var
2961112    ./usr
78944268    ./files
86968424    .
and
> 
# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            239267908 219455708   7753816  97% /
tmpfs                   513056         0    513056   0% /lib/init/rw
varrun                  513056       552    512504   1% /var/run
varlock                 513056         0    513056   0% /var/lock
udev                    513056       148    512908   1% /dev
tmpfs                   513056       164    512892   1% /dev/shm
lrm                     513056      2192    510864   1% /lib/modules/2.6.28-13-generic/volatile


---

### Post by blueridgedog on 2009-06-29
When was the last time the box was rebooted?  The last time I saw something like this, it was due to an apache log file that was locked.  I looked for the thread and could not find it..

---

### Post by IceTerminal on 2009-06-29
> **blueridgedog said:**
> When was the last time the box was rebooted?  The last time I saw something like this, it was due to an apache log file that was locked.  I looked for the thread and could not find it..

I've rebooted it twice this past week. And once this morning actually.

---

### Post by blueridgedog on 2009-06-30
Perhaps and open file that has been unlinked.  What is the output of:

```
lsof +L1
```

---

### Post by blueridgedog on 2009-06-30
As a paranoid thought, you could boot the box on a live CD and test space, just to make certain that you haven't been hacked and have large amount of hidden files which du will not show you.  This is unlikely, but worth checking as you are ruling out possibilities.

Also, looking at this threat:

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/1148574.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1148574.html)

The poster called foonly makes a great summation near the end.  Perhaps it will help.

---

### Post by mcduck on 2009-06-30
5% of disk space on Ext partitions is reserved for root user only (to prevent normal users form filling the drive to the point where the system wouldn't be ableto boot any more). Since you ran the df command as normal user, that 5% doesn't count as available space for you.

Try this:
```

sudo df -h
```

---

### Post by IceTerminal on 2009-06-30
> **blueridgedog said:**
> Perhaps and open file that has been unlinked.  What is the output of:

```
lsof +L1
```


# lsof +L1
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/david/.gvfs
      Output information may be incomplete.
COMMAND   PID     USER   FD   TYPE DEVICE SIZE NLINK    NODE NAME
init        1     root    0u   CHR    5,1          0     608 /dev/console (deleted)
init        1     root    1u   CHR    5,1          0     608 /dev/console (deleted)
init        1     root    2u   CHR    5,1          0     608 /dev/console (deleted)
mysqld   2501    mysql    4u   REG    8,1    0     0 4644879 /tmp/ibYcmIrH (deleted)
mysqld   2501    mysql    5u   REG    8,1    0     0 4644882 /tmp/ibT4oyQ7 (deleted)
mysqld   2501    mysql    6u   REG    8,1    0     0 4644883 /tmp/ibaSUofy (deleted)
mysqld   2501    mysql    7u   REG    8,1    0     0 4644886 /tmp/ibYleoRY (deleted)
mysqld   2501    mysql   11u   REG    8,1    0     0 4644887 /tmp/ibG3Fzaq (deleted)
apache2  3609     root   15w   REG   0,18    0     0    8859 /var/run/apache2/ssl_mutex (deleted)
apache2  3614 www-data   15w   REG   0,18    0     0    8859 /var/run/apache2/ssl_mutex (deleted)
apache2  3711 www-data   15w   REG   0,18    0     0    8859 /var/run/apache2/ssl_mutex (deleted)
apache2  3712 www-data   15w   REG   0,18    0     0    8859 /var/run/apache2/ssl_mutex (deleted)
apache2  3713 www-data   15w   REG   0,18    0     0    8859 /var/run/apache2/ssl_mutex (deleted)
firefox  5293    david   41u   REG    8,1    0     0 8200520 /var/tmp/etilqs_wa2f5DajbBcK3jl (deleted)
apache2 14666 www-data   15w   REG   0,18    0     0    8859 /var/run/apache2/ssl_mutex (deleted)
apache2 14668 www-data   15w   REG   0,18    0     0    8859 /var/run/apache2/ssl_mutex (deleted)
apache2 14669 www-data   15w   REG   0,18    0     0    8859 /var/run/apache2/ssl_mutex (deleted)
apache2 17219 www-data   15w   REG   0,18    0     0    8859 /var/run/apache2/ssl_mutex (deleted)
apache2 21441 www-data   15w   REG   0,18    0     0    8859 /var/run/apache2/ssl_mutex (deleted)
apache2 21472 www-data   15w   REG   0,18    0     0    8859 /var/run/apache2/ssl_mutex (deleted)
apache2 21473 www-data   15w   REG   0,18    0     0    8859 /var/run/apache2/ssl_mutex (deleted)



I've checked the drive and space usage from single user mode, same results.
And I've also ran the df -h as root user and also using the sudo command. Same thing.
I know, its weird.

---

