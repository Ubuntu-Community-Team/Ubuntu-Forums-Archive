---
title: "Hard drive mysteriously full...help!"
date: 2009-11-12
forum: General Help
---

### Post by fonque on 2009-11-12
This morning I tried to check email on my computer, and I received a message that I was low on disk space.

This turned out to be caused by a my syslog and daemon.log files filling up at a ludicrously fast rate. This, I believe was caused by an issue with atftpd not liking my upgrade to Karmic.

I removed atftpd, and managed to clear the two 8.1GB log files. The issue has since not returned. However I am still received low disk space warnings.

When I run disk usage analyzer it says that I have:
used: 13.4GB
available 11.5GB

but "/" directory only shows a size of 5.0 GB, Where is the other 8.4GB???

I also tried running Bleachbit to clean up my disk. Whenever it runs I get a message saying disk full, and it will abort in the middle of cleaning, even though I have 11.5GB free.

How can I track down what is eating my HDD space?

---

### Post by pythonscript on 2009-11-12
Even though the / directory is only shown as using part of that space, have you tried the Disk Usage Analyzer? It's a gui app in Applications -> Accessories -> Disk Usage Analyzer that'll show you a graphical print out of the used space on your system. 

For the sake of posting here, post the output of the

```
sudo du -h --max-depth=1 / | sort -n
```

command. That'll show you what's the biggest directory and sort the output by size.

---

### Post by fonque on 2009-11-12
xxxxxx@xxxxxxxxx:~$ sudo du -h --max-depth=1 / | sort -n
[sudo] password for xxxxxx: 
du: cannot access `/home/xxxxxx/.gvfs': Permission denied
du: cannot access `/proc/5005/task/5005/fd/3': No such file or directory
du: cannot access `/proc/5005/task/5005/fdinfo/3': No such file or directory
du: cannot access `/proc/5005/fd/3': No such file or directory
du: cannot access `/proc/5005/fdinfo/3': No such file or directory
0	/proc
0	/sys
1.6G	/home
2.9G	/usr
4.0K	/mnt
4.0K	/opt
4.0K	/selinux
5.5M	/bin
8.1M	/sbin
16K	/lost+found
16M	/etc
22M	/tmp
40M	/boot
200K	/srv
264G	/media
269G	/
294M	/lib
340M	/var
716K	/dev
1000K	/root



is  /media at 264GB because that is where my 1.5TB drive is mounted?

---

### Post by pythonscript on 2009-11-12
Yes, that's because your hard drive is mounted there. Can you post the output of the previous command on the /usr folder? It seems like that's the largest one, but apart from that, I'm not sure what the problem is.

---

### Post by fonque on 2009-11-13
xxxxxx@xxxxxxxxxx:~$ sudo du -h --max-depth=1 /usr | sort -n
[sudo] password for xxxxxx: 
1.2G	/usr/lib
1.3G	/usr/share
2.8M	/usr/games
2.9G	/usr
18M	/usr/include
25M	/usr/sbin
92K	/usr/lib64
162M	/usr/src
204M	/usr/bin
216K	/usr/local

what are the /usr/lib and /usr/share folders used for?

---

### Post by pythonscript on 2009-11-13
Basically, the /usr/lib folder is for data files that scripts use, but maybe don't execute directly, and /usr/share directory is for static data that applications/scripts, etc use. I can't really give a much better explanation than that, since that's just how it was explained to me (with about the same depth as I'm giving you now). I wouldn't think those would be taking up the space; in my experience, when space starts disappearing mysteriously, it's the /var/log directory that's to blame.

---

### Post by fonque on 2009-11-13
/var/log was my first issue, which I found out was pretty common. After a restart my ubuntu is not displaying any weird behaviour and now has even more free space. I will keep and eye on it for now. I have not received any low disk space messages since yesterday afternoon.

---

### Post by pythonscript on 2009-12-07
Keep us posted if you have any more problems; I've run into problems with /var/log as well, as like you said, this appears to be a (relatively) common problem in ubuntu.

---

### Post by rinrada on 2009-12-08
I have a similar problem. Since upgrading to karmic my HD has been gobbled up by something.

According to Disk Analyser my HD has 127 G with 120 G used, but the analysis of ./ gives only 19.9 G used. So something else is using up 100 G.

Here is the output requested above.

rhett@rhett-eepc:~$ sudo du -h --max-depth=1 / | sort -n
[sudo] password for rhett: 
du: cannot access `/proc/2973/task/2973/fd/4': No such file or directory
du: cannot access `/proc/2973/task/2973/fdinfo/4': No such file or directory
du: cannot access `/proc/2973/fd/4': No such file or directory
du: cannot access `/proc/2973/fdinfo/4': No such file or directory
du: cannot access `/home/rhett/.gvfs': Permission denied

0    /proc
0    /sys
4.0K    /mnt
4.0K    /selinux
4.0K    /srv
4.4G    /usr
5.4M    /bin
8.1M    /sbin
12K    /.cache
14M    /boot
15G    /home
15G    /var
16K    /lost+found
17M    /etc
64K    /tmp
86G    /media
119G    /
119M    /lib
384K    /root
448K    /dev

So it seems that I have lost 86G to /media and 15G to /var.

I did have a external drive attached but it is not connected now, so I don't think it should show anything.
rhett@rhett-eepc:~$ sudo du -h --max-depth=1 /media | sort -n
4.0K    /media/cdrom0
86G    /media
86G    /media/HD-HSU2

rhett@rhett-eepc:~$ sudo du -h --max-depth=1 /var | sort -n
0    /var/lock
4.0K    /var/crash
4.0K    /var/local
4.0K    /var/mail
4.0K    /var/opt
7.8M    /var/backups
14G    /var/backup
15G    /var
16K    /var/games
26M    /var/log
92K    /var/run
220K    /var/spool
286M    /var/lib
547M    /var/cache
888K    /var/tmp

Backups probably useful to keep. Any idea why my HD is full of /media and how to free up this space?

Thanks, Rhett.

---

### Post by lyall on 2009-12-08
if you just deleted the file/s and/or directories they go the the trash can.
there are still on the hard drive and using disk space.
to totally remove them you need to open your trash can.
In Gnome my Trash Can in in the lower right corner of the screen on the bottom bar.

good luck and have fun learning

---

### Post by ed-koala on 2009-12-08
I once had an issue where even though I was deleting trash, it was ending up in root trash and still accumulating, eating up space.

I had to log in as root, go find the root trash can, and empty that sucker out.  I forget now why that even happened but it did "mysteriously" eat up my disk space.

---

### Post by rinrada on 2009-12-12
Thanks. My trash is empty. I'll try to see if the root trash is the problem. Rhett.

---

