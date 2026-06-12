---
title: "no disk space after upgrade to 12.04"
date: 2012-07-27
forum: General Help
---

### Post by Melindrea on 2012-07-27
Hello,

I am now at my wits' end. I have a harddrive that's about ~500G. That has been plenty before, and then the other day I upgraded from 11.10 to 12.04, after which point it started filling up very, very quickly.

I first cleared out old log files, and that sorted it for a few hours. Today I realised that CupsD was spitting out a lot of errors, so removed those logs and fixed the issue. Yet, it continues to complain that there is no harddisk space.

I have removed several files, and I have emptied both root trash and normal trash (I'm the only user on this computer).

According to Disk Usage Analyzer my usage is 486.9 GB/495.4 GB (which still should leave 8.5GB available, and yet I can't even save a textfile that's at most a few KB!). Scanning the filesystem I get that folder / uses 26 GB, where /home is the largest at 17.6GB (I have a lot of crap =), and then user at 5.4GB and var/lib at 2GB.

Can anyone help me figure out where my diskspace is going, or if I should expect that my fairly new harddrive is going to crash any day?

Outputs:
sudo df -h
```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       462G  448G     0 100% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           756M  916K  755M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  896K  1.9G   1% /run/shm
cgroup          1.9G     0  1.9G   0% /sys/fs/cgroup

```

sudo df -i
```

Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda1      30277632 415559 29862073    2% /
udev             481501    522   480979    1% /dev
tmpfs            483702    457   483245    1% /run
none             483702      4   483698    1% /run/lock
none             483702     10   483692    1% /run/shm
cgroup           483702      9   483693    1% /sys/fs/cgroup

```

sudo du -h --max-depth=1 --exclude 'proc' /
```

4.0K	/selinux
367M	/opt
0	/sys
16K	/lost+found
336K	/build
1.8M	/run
4.0K	/srv
9.2M	/sbin
221M	/lib
18M	/etc
12K	/media
4.0K	/mnt
27M	/boot
4.0K	/cdrom
112K	/tmp
5.2G	/usr
du: cannot access `/home/marie/.gvfs': Permission denied
17G	/home
5.1M	/.rpmdb
9.7M	/root
8.9M	/bin
3.4M	/lib32
2.2G	/var
4.0K	/lib64
4.0K	/dev
25G	/

```

---

### Post by Melindrea on 2012-07-27
I'm not sure if this might help, but looking at Deja Dup's settings (this is vaguely based off of [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670) ) I notice that it apparently backed up yesterday, but the folder it was supposed to save in (/home/melindrea/backup) does in fact not exist. I also cannot turn off automatic backups, it does not react when I try to toggle the on/off button.

To really mystify me, I rebooted, and now I have 406G free, which means my plee for help is a lot less urgent, though I would love it if someone can help me figure out why it fills up this way, and/or didn't recognize the change in free space.

---

