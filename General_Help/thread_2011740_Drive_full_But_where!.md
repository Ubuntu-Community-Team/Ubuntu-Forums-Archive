---
title: "Drive full? But where!?"
date: 2012-06-27
forum: General Help
---

### Post by ant2ne on 2012-06-27
Apparently my hard drive is full. But I can't tell where the data is.
```

vmhost:/backup# df -h | grep backup
/dev/sdb1             917G  878G     0 100% /backup

vmhost:/backup# du -h --max-depth=1 ./
9.5G	./remote_webserver
20K	./lost+found
41G	./iso
105M	./local_server
16K	./.Trash-1000
4.1G	./remote_runuo
23M	./remote_rampart
81M	./remote_cygnenos
904G	./

vmhost:/backup# ls -lha
total 850G
drwxrwx--- 10 ant2ne root   4.0K Jun 27 11:41 .
drwxr-xr-x 26 root   root   4.0K Feb 12 11:11 ..
-rwxrwx---  1 ant2ne root     80 Apr 29 21:34 bk2usb.log
-rwxrwx---  1 ant2ne root      0 Jun 20 02:01 bk_files_update.log
-rwxrwx---  1 ant2ne root   684K Jun 27 04:22 bk_files_weekly.log
-rwxrwx---  1 ant2ne root     75 Jun 27 04:24 bkup.err.log
-rwxrwx---  1 ant2ne root    58K Jun 27 04:24 bkup.log
-rwxrwx---  1 ant2ne root   4.3M May 29 05:24 bk_verbose.log
-rwxrwx---  1 ant2ne root   1.5M Nov 29  2010 blocker_squid.dans_2010.11.31.tar
-rwxrwx---  1 ant2ne root   258G Jun 27 04:24 data_drive.tar
-rwxrwx---  1 ant2ne root     56 Apr 24  2011 extract.sc
-rwxrwx---  1 ant2ne root   6.1K Feb 21 14:09 iptables.sc
drwxrwx---  2 ant2ne root   4.0K Mar 16 11:53 iso
-rw-r--r--  1 ant2ne ant2ne 999K Jun 27 11:41 list.tmp
drwxrwx---  4 ant2ne root   4.0K May 24 07:30 local_server
drwxrwx---  2 ant2ne root    20K Apr 27  2011 lost+found
-rwxrwx---  1 ant2ne root      0 Mar 21 02:01 mandi.test.txt
-rwxrwx---  1 ant2ne root   3.1M Oct  7  2011 nohup.out
drwxrwx---  4 ant2ne root   4.0K Jun 28  2011 remote_cygnenos
drwxrwx---  4 ant2ne root   4.0K May  4  2011 remote_rampart
drwxrwx---  2 ant2ne root    12K Jun 25 10:59 remote_runuo
drwxrwx---  3 ant2ne root   4.0K Jul  7  2011 remote_webserver
drwxrwx---  5 ant2ne root   4.0K Jan 14 16:59 .Trash-1000
-rwxrwx---  1 ant2ne root   140G May 16 05:10 VirtualBox.tar

```

---

### Post by Habitual on 2012-06-27
41G    ./iso is a good start.

---

### Post by ajgreeny on 2012-06-27
There are two archive files listed as well, one of 140G the other 258G, so there is almost 400G used by two files.

---

### Post by oldfred on 2012-06-27
Your  ls -lha only is showing the top level. Mine says 48K but I have 49GB in my backup.

 ```
fred@fred-Precise:/media/backup$ ls -lha
total 48K
drwxrwxrwx 10 fred fred 4.0K May 26 17:03 .
drwxr-xr-x  4 root root 4.0K Jun 27 17:58 ..
drwxrw-rw- 15 fred fred  12K Jun 13 15:44 Documents
drwxrw-rw- 15 fred fred 4.0K Mar 24 13:00 Documents2011
drwxr-xr-x  3 root root 4.0K Nov  8  2011 home
drwxr-xr-x  3 root root 4.0K Oct 11  2010 home2011
drwxrw-rw- 33 fred fred 4.0K Jun 13 15:58 Projects
drwxrw-rw- 35 fred fred 4.0K Mar 19 19:23 Projects2011
drwx------  4 root root 4.0K Mar 29  2011 .Trash-0
drwxrwxrwx  5 fred fred 4.0K Aug 21  2009 .Trash-1000
fred@fred-Precise:/media/backup$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd3        28G  8.5G   18G  33% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           791M  1.1M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   76K  2.0G   1% /run/shm
/dev/sda1        55G   36G   20G  65% /mnt/cdrive
/dev/sdc2       100G   29G   71G  30% /mnt/shared
/dev/sdc6        97G   44G   48G  49% /mnt/data
/dev/sda2        74G   49G   22G  70% /media/backup

```

---

### Post by ant2ne on 2012-07-02
[http://forums.debian.net/viewtopic.php?f=10&t=81253&p=441558#p441558]("http://forums.debian.net/viewtopic.php?f=10&t=81253&p=441558#p441558")

the output of 
```

cd/backup
du -hs *
```
directed me to the tar file which reported it was much bigger than the ls. I deleted that file and then did a fsck. The issue seems resolved.

---

