---
title: "Unzipping problem | write error (disk full?)"
date: 2010-04-12
forum: General Help
---

### Post by rodrigogp on 2010-04-12
Hi,

I have a problem with a redhat machine, I'm asking in a redhat forum, but no solution for the moment, I don't know if theres much difference between ubuntu and redhat, but I'm posting my problem here hoping you can help me.

I have a strange problem unzipping a file. I think is a problem of memory or swap space or something similar, I'm going explain the problem in detail:

Distribution:
**Red Hat Enterprise Linux ES release 4 (Nahant Update 3)**

**I'm connected as root.**

I have this zipped file:

```
-rw-r--r--   1 root root 678183271 abr  7 15:30 Master032010.zip
```it contains a 2,4G file


 ```
    df -h
S.ficheros          Tamaño Usado  Disp Uso% Montado en
/dev/cciss/c0d0p6     4,0G  3,5G  282M  93% /
/dev/cciss/c0d0p1     124M   13M  105M  11% /boot
none                  4,0G     0  4,0G   0% /dev/shm
/dev/cciss/c0d0p7      56G   17G   37G  31% /opt
/dev/cciss/c0d0p3     985M   18M  917M   2% /tmp
/dev/cciss/c0d0p5     5,0G  404M  4,3G   9% /var
/dev/sda1             270G  220G   37G  86% /database
/dev/sdb1             125G   63G   56G  54% /data
/dev/sdc1             826G  138G  646G  18% /data2 
```The file is in /dev/sdc1  under /data2/elos/files/in
as you can see this partition has space enough to unzip a 2,4G file
I have also tried to do the same in the /dev/sda1 under /database but in both cases I have the same problem:

 
 ```
    [root@ELOS-BD in]# unzip Master032010.zip 
Archive:  Master032010.zip
  inflating: SongMaster201003.txt    
SongMaster201003.txt:  write error (disk full?).  Continue? (y/n/^C) y
bad CRC 9695f189  (should be 0cab6361) 
```I have typed free:

 ```
    [root@ELOS-BD in]# free -m
             total       used       free     shared    buffers     cached
Mem:          8054       8038         16          0          5       7222
-/+ buffers/cache:        809       7244
Swap:         1023         72 
```I have unzipped the same file in my own machine (ubuntu 9.10) and in windows and I have no problem.


Any idea?

Thanks and regards.

---

### Post by geirha on 2010-04-12
Sounds like unzip on your redhat server is compiled without large file support... [http://en.wikipedia.org/wiki/Large_file_support](http://en.wikipedia.org/wiki/Large_file_support)

---

### Post by rodrigogp on 2010-04-12
Yes, it sounds like this is the problem...

And how can I solve it?

Thanks

---

### Post by geirha on 2010-04-12
Report it as a bug at redhat's bug tracking system.

As a workaround, you can unzip it on a different computer, and copy the files over via ssh, samba, nfs or whatever. Or you can download the source for unzip and build your own unzip package with large file support.

---

### Post by rodrigogp on 2010-04-12
I had thought about unzipping in other machine and upload the unzipped file, but it takes too much time to upload the unzipped file because it is 2,4gb. 

Besides, the problem is that it is a task that should be done by a Java application because the unzipped file need to be processed. This task is repeated 1 time per month.

So I think that I should try to compile the zip program with suppor to large files...

Thanks

---

### Post by geirha on 2010-04-12
Why do you need the unzip command if you're extracting it with java?
[http://java.sun.com/javase/6/docs/api/index.html?java/util/zip/package-summary.html](http://java.sun.com/javase/6/docs/api/index.html?java/util/zip/package-summary.html)

---

### Post by rodrigogp on 2010-04-12
I don't need the unzip command, but I was making tests because when unzipping from java I was having problems, then I tried throught the command line and found this problem... so I've just realized that the problem is not the unzip program

---

### Post by geirha on 2010-04-12
Oh, java stopped at 2GiB too?

---

### Post by rodrigogp on 2010-04-12
No, I have a FileNotFoundException when unziping.... thats because the unzip fails and then I can't create the java File. Trying with files less weight I don't have this problems...

[code]
Unzipping /data2/elos/files/in/Master032010.zip into /database/files/conversor/itunesLoaderTmp
java.io.FileNotFoundException: /database/files/conversor/itunesLoaderTmp/SongMaster201003.txt (No such file or directory)
    at java.io.FileOutputStream.open(Native Method)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
    at elos.master.util.Unzip.unzipEntry(Unzip.java:145)
    at elos.master.util.Unzip.unzip(Unzip.java:96)
    at elos.master.util.Unzip.unzip(Unzip.java:72)
    at elos.master.itunes.ITunesFileLoaderImpl.execute(ITunesFileLoaderImpl.java:102)
    at elos.master.action.FileLoaderAction$LoaderThread.run(FileLoaderAction.java:76)
    at java.lang.Thread.run(Thread.java:534)
Unzipping /data2/elos/files/in/MasterA032010.zip into /database/files/conversor/itunesLoaderTmp
java.io.FileNotFoundException: /database/files/conversor/itunesLoaderTmp/AlbumMaster201003.txt (No such file or directory)
    at java.io.FileOutputStream.open(Native Method)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
    at elos.master.util.Unzip.unzipEntry(Unzip.java:145)
    at elos.master.util.Unzip.unzip(Unzip.java:96)
    at elos.master.util.Unzip.unzip(Unzip.java:72)
    at elos.master.itunes.ITunesFileLoaderImpl.execute(ITunesFileLoaderImpl.java:102)
    at elos.master.action.FileLoaderAction$LoaderThread.run(FileLoaderAction.java:76)
    at java.lang.Thread.run(Thread.java:534)[code]

---

