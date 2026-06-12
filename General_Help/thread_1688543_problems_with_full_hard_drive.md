---
title: "problems with full hard drive"
date: 2011-02-15
forum: General Help
---

### Post by cjustinc on 2011-02-15
So my Ubuntu lives on a pretty small (~30 GB) solid state, and a few days ago I started getting messages to the effect that my hard drive is full (I can't even save text files!). However, when I run the disk usage analyzer I can't locate most of the data: the disparity seems to be between the total for my /home directory (~20 GB) and the sum over all the files and subdirectories it contains (no more than 5 GB). What's going on?

On a possibly related note: recently I tried to delete some large video files on another hard drive, and probably did it in a stupid way, because they ended up in my trash folder. When I tried to delete them permanently from the trash, nothing happened, and now when I try I get the error message "No such file or directory." Any suggestions? Thanks.

---

### Post by TeoBigusGeekus on 2011-02-15
It was probably an external hard drive. Plug it in, mount it and try emptying your trash again.

Can you post us the output of 
```
df -h
```
?

---

### Post by cjustinc on 2011-02-15
It's an internal hard drive. When it's mounted df -h gives me

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              29G   27G     0 100% /
udev                 1005M  296K 1005M   1% /dev
none                 1005M  844K 1004M   1% /dev/shm
none                 1005M  328K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
/dev/sdc2              51G   39G   13G  75% /media/CE94C1CF94C1BA6B

---

### Post by TeoBigusGeekus on 2011-02-15
Your root partition is almost full.
Post us the output of
```
sudo du -h / --max-depth=1 | sort -h
```

For your trash, try
```
sudo rm ~/.local/share/Trash/files/*
```

---

### Post by cjustinc on 2011-02-15
The first command gets me "sort: invalid option -- 'h'." 

The second one gets "rm: cannot remove `/home/cjustinc/.local/share/Trash/files/*': No such file or directory."

---

### Post by TeoBigusGeekus on 2011-02-15
1)Try again without the sort pipe.

2)Go to your internal hd where the files originally belonged. Find the .Trash folder in there (could something like .Trash1000). Select it and delete it. Then try again emptying your trash.

---

### Post by cjustinc on 2011-02-15
When I leave out sort I get

16M	/etc
2.2G	/tmp
3.8G	/usr
38G	/media
13M	/lib32
4.0K	/mnt
200K	/srv
395M	/var
16K	/lost+found
88M	/opt
7.7M	/sbin
du: cannot access `/home/cjustinc/.gvfs': Permission denied
20G	/home
5.8M	/bin
du: cannot access `/proc/32720/task/32720/fd/3': No such file or directory
du: cannot access `/proc/32720/task/32720/fdinfo/3': No such file or directory
du: cannot access `/proc/32720/fd/3': No such file or directory
du: cannot access `/proc/32720/fdinfo/3': No such file or directory
0	/proc
86M	/boot
1.4M	/root
996K	/dev
4.0K	/selinux
0	/sys
705M	/lib
65G	/

As for the other hard drive, I don't think there is a .Trash folder (it has my old Windows XP on it). The files don't appear on that hard drive at all.

---

### Post by TeoBigusGeekus on 2011-02-16
Install bleachbit and do a clean up as user and as root.

While on the other drive with nautilus, press ctrl-h to reveal hidden folders in order to see if there is a .Trash folder.

---

