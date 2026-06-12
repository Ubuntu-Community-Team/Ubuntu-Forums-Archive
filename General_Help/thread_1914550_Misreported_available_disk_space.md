---
title: "Misreported available disk space"
date: 2012-01-24
forum: General Help
---

### Post by dargaud on 2012-01-24
Hello all,
I just plugged in my usual external backup disk and... there's no space left on it. Even if I delete some stuff ! It's an ext4 partition.
```
# df -k
/dev/sde1            1442145212 1369136212         0 100% /media/External

```
As you see there should be 69Gb available. I can 'touch' new files but I cannot put anything in them: no space left on device. And yes, the first thing I did was to unmount it and run fsck on it: no change.

> # fsck -C /dev/sde1
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
External has been mounted 33 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts                                              
Pass 5: Checking group summary information                                     
External 748599/91578368 files (3.0% non-contiguous), 348164246/366284000 blocks

What's going on ?!?

---

### Post by BC59 on 2012-01-24
Silly question but did you empty your trash?

---

### Post by dargaud on 2012-01-24
There's no thrash on this disk, and I used rm-rf to delete the files:
```
$ ls -alF
total 24
drwxr-xr-x  5 dargaud users   4096 2012-01-24 20:13 ./
drwxr-xr-x  5 root    root    4096 2012-01-24 21:20 ../
drwxrwxrwx  6 dargaud dargaud 4096 2011-07-21 00:24 Backup/
-rw-------  1 dargaud users     49 2010-10-13 01:18 .directory
drwxrwxr-x 18 dargaud dargaud 4096 2011-10-27 15:51 Data/
drwx------  2 root    root    4096 2009-04-01 00:27 lost+found/

```

---

### Post by BC59 on 2012-01-24
There is a very good thread about this:

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by dargaud on 2012-01-24
Thanks, the solution was on that page (tune2fs -m). Though I have no idea why there were reserved blocks on that disk:
```
$ sudo tune2fs -l /dev/sde1
...
Block count:              366284000
Reserved block count:     18314200
Free blocks:              18252250
...

$ sudo tune2fs -m 0 /dev/sde1                                                                                              
tune2fs 1.41.14 (22-Dec-2010)                                                                                                
Setting reserved blocks percentage to 0% (0 blocks)                                                                          

$ df 
/dev/sde1            1442145212 1369136212  73009000  95% /media/External

```

---

