---
title: "Ive lost my lost folder"
date: 2010-06-25
forum: General Help
---

### Post by w1z4rd on 2010-06-25
Setup:

Normal laptop with two partitions, Ubuntu Lucid and Windows 7.

I get an external and plug it in, since I hardly use my Windows partition I decided to copy all 6 seasons of lost from my external onto my Windows partition.

In the root of my windows partition I created a folder called "media" and copied all the lost seasons onto it.

The copy went fine, and took its time (it was 50 GBs large or so).

Once it had copied I decided to play some HON. 

I rebooted my laptop and decided I wanted to watch some media... but all of a sudden.. the media folder I created on the windows partition is missing... but all the space is being used up!

Let me show you my problem in command line results:

> root@dave-laptop:/media# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             70787488  23762692  43428972  36% /
none                    991408       308    991100   1% /dev
none                    995624      3128    992496   1% /dev/shm
none                    995624       196    995428   1% /var/run
none                    995624         0    995624   0% /var/lock
none                    995624         0    995624   0% /lib/init/rw
/dev/sda1               102396     24712     77684  25% /media/System Reserved
/dev/sda2             81168772  67022240  14146532  83% /media/52405B31405B1AD5


You can clearly see there that 67GBs or so are being used on my Windows partition. Since it only has a flat W7 install with Office and one game installed, there should not be a lot of space used up. Certainly not 83% of the partition.

So in an effort to find my missing folder I du:

> root@dave-laptop:/media# du -sh /media/52405B31405B1AD5/*
512	/media/52405B31405B1AD5/autoexec.bat
4.0K	/media/52405B31405B1AD5/bootsqm.dat
512	/media/52405B31405B1AD5/config.sys
0	/media/52405B31405B1AD5/Documents and Settings
1.5G	/media/52405B31405B1AD5/hiberfil.sys
529M	/media/52405B31405B1AD5/MSOCache
2.0G	/media/52405B31405B1AD5/pagefile.sys
0	/media/52405B31405B1AD5/PerfLogs
246M	/media/52405B31405B1AD5/ProgramData
1.8G	/media/52405B31405B1AD5/Program Files
444K	/media/52405B31405B1AD5/Putty
142M	/media/52405B31405B1AD5/Recovery
7.5K	/media/52405B31405B1AD5/$Recycle.Bin
1.2G	/media/52405B31405B1AD5/System Volume Information
2.4G	/media/52405B31405B1AD5/Users
4.7G	/media/52405B31405B1AD5/Windows


As you can see, the math does not add up! Ive lost my lost and worst... Ive got 50 odd GBs of used disk space I cant recover!

Any ideas?

---

### Post by justleen on 2010-06-25
look for hidden folders, starting with a "."

```

ls -la /media/52405B31405B1AD5
du -hs /media/52405B31405B1AD5/.*

```

---

### Post by w1z4rd on 2010-06-25
Run them all...

> **root@dave-laptop:/media# ls -la /media/52405B31405B1AD5**
total 3544669
drwx------ 1 dave dave       4096 2010-06-25 09:27 .
drwxr-xr-x 4 root root       4096 2010-06-25 12:30 ..
-rwxrwxrwx 1 dave dave         24 2009-06-10 23:42 autoexec.bat
-rwxrwxrwx 1 dave dave       3304 2010-06-08 21:38 bootsqm.dat
-rwxrwxrwx 1 dave dave         10 2009-06-10 23:42 config.sys
lrwxrwxrwx 2 dave dave         60 2009-07-14 06:53 Documents and Settings -> /media/52405B31405B1AD5/Users
-rwxrwxrwx 1 dave dave 1555578880 2010-06-25 10:30 hiberfil.sys
drwx------ 1 dave dave          0 2010-06-25 12:10 MSOCache
-rwxrwxrwx 1 dave dave 2074107904 2010-06-25 10:30 pagefile.sys
drwx------ 1 dave dave          0 2009-07-14 04:37 PerfLogs
drwx------ 1 dave dave       4096 2010-06-08 22:06 ProgramData
drwx------ 1 dave dave      12288 2010-06-25 09:26 Program Files
drwx------ 1 dave dave          0 2010-06-08 21:55 Putty
drwx------ 1 dave dave          0 2010-06-08 19:05 Recovery
drwx------ 1 dave dave          0 2010-06-08 19:06 $Recycle.Bin
drwx------ 1 dave dave       4096 2010-06-25 09:27 System Volume Information
drwx------ 1 dave dave       4096 2010-06-08 19:06 Users
drwx------ 1 dave dave      16384 2010-06-08 22:09 Windows
**root@dave-laptop:/media# du -hs /media/52405B31405B1AD5/.***
23G	/media/52405B31405B1AD5/.
16G	/media/52405B31405B1AD5/..
**root@dave-laptop:/media# du -sh /media/52405B31405B1AD5/***
512	/media/52405B31405B1AD5/autoexec.bat
4.0K	/media/52405B31405B1AD5/bootsqm.dat
512	/media/52405B31405B1AD5/config.sys
0	/media/52405B31405B1AD5/Documents and Settings
1.5G	/media/52405B31405B1AD5/hiberfil.sys
8.6G	/media/52405B31405B1AD5/MSOCache (ignore this folder, I just copied the data there)
2.0G	/media/52405B31405B1AD5/pagefile.sys
0	/media/52405B31405B1AD5/PerfLogs
246M	/media/52405B31405B1AD5/ProgramData
1.8G	/media/52405B31405B1AD5/Program Files
444K	/media/52405B31405B1AD5/Putty
142M	/media/52405B31405B1AD5/Recovery
7.5K	/media/52405B31405B1AD5/$Recycle.Bin
1.2G	/media/52405B31405B1AD5/System Volume Information
2.4G	/media/52405B31405B1AD5/Users
4.7G	/media/52405B31405B1AD5/Windows
**root@dave-laptop:/media# df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              68G   58G  6.3G  91% /
none                  969M  308K  968M   1% /dev
none                  973M  2.7M  970M   1% /dev/shm
none                  973M  196K  973M   1% /var/run
none                  973M     0  973M   0% /var/lock
none                  973M     0  973M   0% /lib/init/rw
/dev/sda1             100M   25M   76M  25% /media/System Reserved
/dev/sda2              78G   72G  5.5G  93% /media/52405B31405B1AD5


No hidden folders or anything. This is the most confusing thing ever.

---

### Post by justleen on 2010-06-25
The folder you lost, was it in the root of the drive??

---

### Post by w1z4rd on 2010-06-25
Yeah it was. Will that effect it some way?

---

### Post by SlugSlug on 2010-06-25
might help..?

```
cd /
```
```
find . -name *.avi
```
or
```
find . -type d -name *ost
```

---

### Post by justleen on 2010-06-25
> **w1z4rd said:**
> Yeah it was. Will that effect it some way?

No it wont effect it in some way, just that we are listing the root all the time, thus if it wasn't in root, we could look there for ever..

---

### Post by w1z4rd on 2010-06-25
> **SlugSlug said:**
> might help..?

```
cd /
```
```
find . -name *.avi
```
or
```
find . -type d -name *ost
```

Nope. Nothing found.

I suspect the file indexing is broke.

---

