---
title: "Searching Your Hard Drive"
date: 2011-05-17
forum: General Help
---

### Post by ron177 on 2011-05-17
What is the best way to locate a file or folder in your hard drive? I have been trying to do that through searching in "Files & Folders" but it seems that the search is not thorough: it doesn't look for everything. I have an external drive that when it's connected to the computer I would like to search inside of it as well. The "Files & Folders" option does not seem to do that at all.

---

### Post by hwttdz on 2011-05-17
Personally I use the find command on the command line.  If you know that a given file lies below a point on the filesystem you can do
find . -iname "*partoffilename*" -type f
"man find" will give you full usage, and it's really quite powerful (and confusing and complicated), so if you're interested in using it and are having difficulty getting it to do exactly what you want feel free to ask questions.

---

### Post by TeoBigusGeekus on 2011-05-17
Look at find command
```
man find
```
If, for example, you want to find all your jpgs on your external hd, you could
```
find /media/HDmountpoint -iname "*.jpg"
```

---

### Post by WorMzy on 2011-05-17
An quick and easy way to search your local partition (/) is locate.

```
locate filename
```

You may want to run
```
sudo updatedb
```
first, if the file you're searching for has been created in your current session, or if you've moved it.

---

### Post by lithopsian on 2011-05-17
find is powerful and slow but doesn't miss files.  It is usually best when you only need to search a small portion of your file system.  Searching a large file system from scratch will take many minutes at best.

locate is fast, has limited capabilities, and can miss stuff.  locate runs off a database which needs to be updated to keep track of all your files.  This is generally done each day by a cron job.

---

### Post by TeoBigusGeekus on 2011-05-17
No, I wouldn't say minutes.
Here's a df -h of my system
```
[[Time:23:43 Location:~/Desktop]]
$ df -h
Filesystem                                              Size  Used Avail Use% Mounted on
udev                                                     10M     0   10M   0% /dev
run                                                      10M  184K  9.9M   2% /run
/dev/disk/by-uuid/297ff4d0-e14b-41a4-8631-0b6e4cbe154b   28G  2.9G   23G  12% /
shm                                                     502M     0  502M   0% /dev/shm
/dev/sda3                                                46G   14G   30G  31% /home
/dev/sdc1                                               294G  210G   69G  76% /media/disk
/dev/sdb1                                               276G  162G  100G  62% /media/disk-1
```
and here's the output of a timed find command searching through the entire file system
```
time find / -iname "*.jpg" 2>/dev/null
....
(Hiddeously long list of jpgs)
....

real    0m25.434s
user    0m0.917s
sys     0m1.767s
```

---

### Post by WorMzy on 2011-05-17
Depends how many file systems you have mounted.

```
Filesystem                                              Size  Used Avail Use% Mounted on
udev                                                     10M     0   10M   0% /dev
run                                                      10M  256K  9.8M   3% /run
/dev/disk/by-uuid/d2ce5ccb-4b0b-42c4-a028-15c3331c4ba2   37G   18G   18G  51% /
shm                                                     2.0G  2.9M  2.0G   1% /dev/shm
/dev/sda1                                               652G  423G  229G  65% /home/wormzy/Videos
/dev/sdb1                                               932G  294G  639G  32% /media/Terastore
/dev/sdd7                                                37G  1.1G   34G   3% /media/Arch64-Open
/dev/sdd9                                                37G   26G  9.5G  73% /media/Arch32
```

2.81s user
7.26s system
5:06.93 total

---

