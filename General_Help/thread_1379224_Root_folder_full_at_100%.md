---
title: "Root folder full at 100%"
date: 2010-01-12
forum: General Help
---

### Post by lsutiger on 2010-01-12
My root folder is full. I searched through the folder using the CLI and could not find anything that would take up all 9.7GB. I read a few threads already that said empty the trash for root, which I did and nothing changed.
There were also some things in the tmp folder, which I did not touch. I cleaned up apt, hardly nothing changed with that.

I believe this is from an automated backup that did not have access to the network drive, but I can not find the file that is taking up all the place.
Please help!

---

### Post by chrisinspace on 2010-01-12
Can you get into the GUI desktop?  If so, the Disk Usage Analyzer might help you find the culprit.  If find it to be a very useful tool.

---

### Post by lsutiger on 2010-01-12
Thank you for your response, but the disk analyzer doesn't show me any new information. Shows / at 100% but does not tell what is taking up that space.
I have / and /home on different partitions.
Here is the listing:
 ```
brian@brian-linux:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  9.0G     0 100% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  356K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  160K 1007M   1% /dev
tmpfs                1007M  5.3M 1002M   1% /dev/shm
lrm                  1007M  2.2M 1005M   1% /lib/modules/2.6.28-17-generic/volatile
/dev/sda2              62G   54G  5.4G  91% /home

```
but when I browse through the / folder I can not find anything that adds up t0 9.7GB

---

### Post by michy99 on 2010-01-12
If you did a backup to a disk that wasn't mounted, then unmount that disk now and look in the directory that it mounts to. You should find a backup there that is actually on your root partition.

---

### Post by lsutiger on 2010-01-12
Thanx michy99. I tried to do what you said.
The backup folder is /mnt/backup. I umount that folder and listed the contents:
```
 sudo umount /mnt/backup
cd /mnt/backup
ls -al
total 8
drwxr-xr-x 11 root root 4096 2009-07-29 13:11 ..
drwxr-xr-x  2 root root 4096 2009-06-02 12:32 .
du -h
4.0K	.

```

Nothing there.

---

### Post by sisco311 on 2010-01-12
You can use the du command to print the size of the directories:
```
sudo du -ch --max-depth=1 --exclude=/home/ /
```

---

### Post by michy99 on 2010-01-12
Maybe you just have a lot of stuff installed. My / partition is approaching 7G and I really don't have a whole lot of extras installed compared to some people.

---

### Post by darco on 2010-01-12
There can be many reasons why the /root folder will suddenly "fill up". I know when I have my vmware machine open and have transferred files from it to my hdd that a temp folder will be left behind and fill up my /root folder. 
My root is is 10gb and never gets past 4gb so when it does fill up, I know there is something wrong.
Check this link

[http://ubuntuforums.org/showthread.php?t=1088911&highlight=root+disk+space](http://ubuntuforums.org/showthread.php?t=1088911&highlight=root+disk+space)

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

darco

---

### Post by lsutiger on 2010-01-12
Michy99 - this happened overnight. 
sisco - I tried what you suggested and came up with some interesting info:
```
du -ch --max-depth=1 --exclude=/home/ 2> /dev/null
4.9G	./var
3.2G	./usr
8.3M	./sbin
145M	./opt
16K	./lost+found
54G	./home
4.0K	./selinux
16K	./tmp
146G	./mnt
5.1M	./dev
592M	./lib
4.0K	./srv
76M	./boot
0	./sys
6.0M	./bin
0	./proc
20K	./media
15M	./etc
4.0K	./root
209G	.
209G	total

```
4.9GB in var??
so I cd to var:
```
du -ch --max-depth=1 --exclude=/home/ 2> /dev/null
6.2M	./backups
4.0K	./usr
0	./lock
352K	./run
4.0K	./sbin
45M	./log
4.0K	./opt
4.3G	./home
540K	./tmp
357M	./lib
4.0K	./local
76M	./boot
4.0K	./games
192K	./spool
56M	./cache
6.0M	./bin
15M	./etc
4.0K	./mail
4.0K	./crash
4.9G	.
4.9G	total

```

What's that 4.9G with a dot next to it??
when I list the directory:
```
ls -al
total 84
drwxr-xr-x  19 root root    740 2010-01-12 10:40 run
drwxrwxrwt   2 root root     80 2010-01-12 10:34 lock
drwxrwxrwt   3 root root   4096 2010-01-12 10:08 tmp
drwxr-xr-x  15 root root   4096 2010-01-12 10:06 log
drwxr-xr-x  21 root root   4096 2010-01-07 08:11 ..
drwxr-xr-x 151 root root  12288 2010-01-06 19:16 etc
drwxr-xr-x   2 root root   4096 2010-01-06 08:05 backups
drwxr-xr-x   4 root root   4096 2009-12-28 16:14 home
drwxr-xr-x   2 root root   4096 2009-12-28 12:45 bin
drwxr-xr-x   3 root root   4096 2009-12-28 12:45 boot
drwxr-xr-x  21 root root   4096 2009-12-28 12:45 .
drwx------   2 root root   4096 2009-12-28 12:45 sbin
drwx------   2 root root   4096 2009-12-28 12:45 usr
drwxr-xr-x  63 root root   4096 2009-08-24 09:43 lib
drwxr-xr-x  18 root root   4096 2009-08-24 09:43 cache
drwxr-xr-x   8 root root   4096 2009-06-04 16:15 spool
drwxr-xr-x   2 root root   4096 2009-06-02 10:05 crash
drwxr-xr-x   2 root root   4096 2009-06-02 10:05 games
drwxrwsr-x   2 root staff  4096 2009-06-02 10:05 local
drwxrwsr-x   2 root mail   4096 2009-06-02 10:05 mail
drwxr-xr-x   2 root root   4096 2009-06-02 10:05 opt

```
I do not see any 4.9 GB file...

---

### Post by wojox on 2010-01-12
> What's that 4.9G with a dot next to it??

That's your var folder.

---

### Post by Onesimus on 2010-01-12
Do you get any further directories / files appearing if you type

```
ls -al /var
```

---

### Post by Onesimus on 2010-01-12
Sorry you've already done this !

---

### Post by Onesimus on 2010-01-12
It appears that there is a directory called home in your var directory.  Could that be your problem ?

---

### Post by lsutiger on 2010-01-12
> Onesimus  	

It appears that there is a directory called home in your var directory. Could that be your problem ? 
DING!DING!DING!DING!DING!DING!DING!!! WE HAVE A WINNER!:D
That is where the backup was stored when the network connection failed! Removed and back to 4.7GB free!
Thanx a lot for all of your help!

---

### Post by sisco311 on 2010-01-12
> **lsutiger said:**
> DING!DING!DING!DING!DING!DING!DING!!! WE HAVE A WINNER!:D
That is where the backup was stored when the network connection failed! Removed and back to 4.7GB free!
Thanx a lot for all of your help!

Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

### Post by lsutiger on 2010-01-12
Oh that's back? Kewl...

---

