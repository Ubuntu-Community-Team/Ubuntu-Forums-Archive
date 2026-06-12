---
title: "No more spcace on root..."
date: 2011-01-18
forum: General Help
---

### Post by Tuvok41 on 2011-01-18
Well I have a big problem, I had the backup utility saving them on a usb drive, at one point I think my son must have unplugged it, it then created a virtual drive with same name as the one that was supposed to be there, forgot to tick the do not perform backup if destination does not exist :(.

I had time to see the mounted drive, using all my space close to 12GB, it did a few backups, as I set it daily, by the time I figured what happened, was going to view a movie on that drive, but didnt see my movies only the backup folders, I rebooted with the usb drive plugged this time, but no more of that mounted drive it did previously and now all my space gone, cannot download updates, files, nor can I view any youtubes, is there a way I can regain that space, I dont really need the files that were created since I have the last one created on the usb drive, so I could careless about the data, just want my space back :(

MountManager will not start, so I can't manage it, if it is there, or there is one drive not present it would probably had fixed it, but no can do :(


```

 sudo df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1             13938824  13349520         0 100% /
tmpfs                  1548520         0   1548520   0% /lib/init/rw
varrun                 1548520       224   1548296   1% /var/run
varlock                1548520         0   1548520   0% /var/lock
udev                   1548520       204   1548316   1% /dev
tmpfs                  1548520      1228   1547292   1% /dev/shm
lrm                    1548520      2192   1546328   1% /lib/modules/2.6.28-19-generic/volatile
/dev/sdc6             60997956    696172  57203252   2% /home
/dev/sdg1            976760000 970003108   6756892 100% /media/HDD1000D1_
/dev/sdh1            976760000 946646580  30113420  97% /media/HDD1000D3
/dev/sda1            732572000 732572000         0 100% /media/HDD750D1
/dev/sdb1            732572000 726481788   6090212 100% /media/HDD750D2
/dev/sdd1            312568640 202380768 110187872  65% /media/SHARE_TOONS
/dev/sdc5             78140128   4711524  73428604   7% /media/sde5
overflow                  1024       784       240  77% /tmp
/dev/sdf1            976760000 955859992  20900008  98% /media/HDD1000D2_
```


```
sudo ls / -all -s
total 100
 4 drwxr-xr-x  21 root root  4096 2010-08-12 04:35 .
 4 drwxr-xr-x  21 root root  4096 2010-08-12 04:35 ..
 4 drwxr-xr-x   2 root root  4096 2010-03-25 23:17 bin
 4 drwxr-xr-x   3 root root  4096 2010-09-19 07:21 boot
 0 lrwxrwxrwx   1 root root    11 2009-11-23 03:56 cdrom -> media/cdrom
 0 drwxr-xr-x  15 root root  4640 2011-01-17 02:10 dev
12 drwxr-xr-x 165 root root 12288 2011-01-15 09:39 etc
 4 drwxr-xr-x   5 root root  4096 2008-10-20 08:27 home
 0 lrwxrwxrwx   1 root root    33 2010-06-03 13:19 initrd.img -> boot/initrd.img-2.6.28-19-generic
 0 lrwxrwxrwx   1 root root    33 2010-03-25 23:37 initrd.img.old -> boot/initrd.img-2.6.28-18-generic
12 drwxr-xr-x  18 root root 12288 2010-09-19 08:16 lib
16 drwx------   4 root root 16384 2009-11-23 03:56 lost+found
 4 drwxr-xr-x  17 root root  4096 2011-01-15 09:39 media
 4 drwxr-xr-x   2 root root  4096 2008-10-20 08:27 mnt
 4 drwxr-xr-x   4 root root  4096 2009-12-22 16:16 opt
 0 dr-xr-xr-x 164 root root     0 2011-01-15 09:44 proc
 4 drwxr-xr-x  17 root root  4096 2010-10-14 10:08 root
 4 drwxr-xr-x   2 root root  4096 2010-09-19 08:16 sbin
 4 drwxr-xr-x   2 root root  4096 2009-03-06 11:21 selinux
 4 -rw-r--r--   1 root root  2982 2010-08-12 04:35 sources.list.backup
 4 drwxr-xr-x   2 root root  4096 2008-10-29 18:53 srv
 0 drwxr-xr-x  12 root root     0 2011-01-15 09:44 sys
 0 drwxrwxrwt  22 root root   480 2011-01-17 23:49 tmp
 4 drwxr-xr-x  13 root root  4096 2010-03-25 23:26 usr
 4 drwxr-xr-x  17 root root  4096 2010-02-17 11:08 var
 0 lrwxrwxrwx   1 root root    30 2010-06-03 13:19 vmlinuz -> boot/vmlinuz-2.6.28-19-generic
 0 lrwxrwxrwx   1 root root    30 2010-03-25 23:37 vmlinuz.old -> boot/vmlinuz-2.6.28-18-generic

```

---

### Post by Bitrate on 2011-01-18
If you can get to a terminal then issue this command to see what the disk usage is:

sudo du -sh /[!d,p]*

From their you should be able to narrow down the directories which are taking up space on root.

---

### Post by Tuvok41 on 2011-01-18
> **Bitrate said:**
> If you can get to a terminal then issue this command to see what the disk usage is:

sudo du -sh /[!d,p]*

From their you should be able to narrow down the directories which are taking up space on root.

Thx, it did give me this as output so far, still waiting for it to finish,

```
 sudo du -sh /[!d,p]*
6.1M    /bin
26M    /boot
0    /cdrom
18M    /etc
du: cannot access `/home/theary/.gvfs': Permission denied
502M    /home
0    /initrd.img
0    /initrd.img.old
239M    /lib
208K    /lost+found
du: cannot access `/media/HDD1000D3/BackupUbuntu.09.05.2010/2010-06-14_05.00.02.683911.theary-desktop.inc': Input/output error
du: cannot access `/media/HDD1000D3/BackupUbuntu.09.05.2010/2010-06-18_05.00.02.677631.theary-desktop.ful/fprops': Input/output error
du: cannot access `/media/HDD1000D3/Les.Boys.IV.nogood/LES_BOYS_IV.iso': Input/output error
4.3T    /media
4.0K    /mnt
52K    /opt
1.1M    /root
7.0M    /sbin
4.0K    /selinux
4.0K    /sources.list.backup
4.0K    /srv
0    /sys
784K    /tmp
3.6G    /usr
5.8G    /var
0    /vmlinuz
0    /vmlinuz.old


```


It looks like they are files that are on a media which is not mounted :```
sudo ls ../media/HDD1003D3 -all -s --group -c -l -h
ls: cannot access ../media/HDD1003D3: No such file or directory

```

---

### Post by Krytarik on 2011-01-18
There is far too much space spent on the "/var" directory:
```
5.8G /var
```Maybe it's the "tmp" subdirectory. Narrow it down by entering the "var" directory and issuing the command:
```
sudo du -sh *
```This command is to also show hidden dirs/files, which should not be the case in the "var" dir:
```
sudo du -sh .[!.]* *| sort -n
```And you should use the "-x" option when doing "du" on the root directory.

[http://linux.die.net/man/1/du](http://linux.die.net/man/1/du)

PS: I've just yet found that my home dir occupies more than 700 megs, I have to search for culprit now.;-)

---

### Post by Tuvok41 on 2011-01-18
> **Krytarik said:**
> There is far too much space spent on the "/var" directory:
```
5.8G /var
```Maybe it's the "tmp" subdirectory. Narrow it down by entering the "var" directory and issuing the command:
```
sudo du -sh *
```This command is to also show hidden dirs/files, which should not be the case in the "var" dir:
```
sudo du -sh .[!.]* *| sort -n
```And you should use the "-x" option when doing "du" on the root directory.

[http://linux.die.net/man/1/du](http://linux.die.net/man/1/du)

PS: I've just yet found that my home dir occupies more than 700 megs, I have to search for culprit now.;-)

Thx, found mine, I found it in backup, was a 4.4GB culprit ;)

---

