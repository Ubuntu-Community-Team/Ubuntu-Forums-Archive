---
title: "Disk filling up, disparity between df &amp; du"
date: 2011-02-19
forum: General Help
---

### Post by rm-rf on 2011-02-19
For a while my root partition has been filling up for no apparent reason. I I have been deleting things to find out it fills up again in a mater of days. To make it more 'interesting', there is a disparity between what I get from df and what the du command is telling me. After dismounting the other file systems and turning off applications, this is what i get:

output of df -ha
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdf5              69G   66G   54M 100% /
proc                     0     0     0   -  /proc
none                     0     0     0   -  /sys
none                  2.0G  348K  2.0G   1% /dev
none                     0     0     0   -  /dev/pts
none                  2.0G  312K  2.0G   1% /dev/shm
none                  2.0G  332K  2.0G   1% /var/run
rpc_pipefs               0     0     0   -  /var/lib/nfs/rpc_pipefs
nfsd                     0     0     0   -  /proc/fs/nfsd
```

output of du -sch *
```

7.8M	bin
4.0K	boot
628K	boot.tmp
4.0K	cdrom

660K	dev
17M	etc
22G	home
0	initrd.img
0	initrd.img.old
451M	lib
13M	lib32
0	lib64
16K	lost+found
4.0K	media
8.0K	mnt
164M	opt
du: cannot access `proc/17151/task/17151/fd/4': No such file or directory
du: cannot access `proc/17151/task/17151/fdinfo/4': No such file or directory
du: cannot access `proc/17151/fd/4': No such file or directory
du: cannot access `proc/17151/fdinfo/4': No such file or directory
0	proc
1.8G	root
7.6M	sbin
4.0K	selinux
200K	srv
0	sys
13M	tmp
3.9G	usr
543M	var
0	vmlinuz
0	vmlinuz.old
4.0K	xorg.conf.new
29G	total

```

du claims that I'm using 29G on that partition, which sounds about right (this is my OS and basic /home partition, everything else is elsewhere). df on the other hand is telling me here that out of 69G, 64G are in use with only 54M left. Actually by the time I finished typing this post it ate the last 54 megs :\

Any clues are welcome.

---

### Post by rm-rf on 2011-02-20
Anybody?

I can't find where the disk space is going! As soon as I delete something, it slowly banishes into thin air :confused:

I disconnected the network in case somebody was using my disk space. Erased a big file, and still the same. doing a 'watch -n df' I can see the disk space disappearing. doing a 'watch 'du -sc *' I don't see the space being used anywhere.

The only thing that changes in the du command is the error message, where the number (in this case  9565) keeps growing up:
```

du: cannot access `proc/9565/task/9565/fd/5': No such file or directory
du: cannot access `proc/9565/task/9565/fdinfo/5': No such file or directory
du: cannot access `proc/9565/fd/5': No such file or directory
du: cannot access `proc/9565/fdinfo/5': No such file or directory
```

which I have no clue what it means (I know what /proc is).

Help? Pretty please?

---

### Post by rm-rf on 2011-02-20
Ok, the disk space bleeding stopped. Upon some research I found about iotop, which allowed me to look at who was writing to my disks. The culprit was on the following line:

```

TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND                      
3679 be/4 bob         0.00 B/s   73.93 K/s  ?unavailable?  npviewer.bin --plugin /usr/lib/flashplugin-installer~tion /org/wrapper/NSPlugins/libflashplayer.so/2349-4
```

So, killing the process npviewer.bin stopped the leeching. Now the question is; where the * is the stolen drive space? It isn't under /var/log errors or any other place i would think it would be...

---

