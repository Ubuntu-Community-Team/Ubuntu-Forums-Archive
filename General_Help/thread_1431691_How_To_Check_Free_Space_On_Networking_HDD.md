---
title: "How To Check Free Space On Networking HDD"
date: 2010-03-16
forum: General Help
---

### Post by warrior_juggalo on 2010-03-16
I can't seem to find anywhere to find how much free space i have on my "my book world edition II", Unlike normal HDD's when you just right click and it shows the Yellow and blue circle, Please help!!!

---

### Post by darolu on 2010-03-16
Have you tried with?
```
sudo df /dev/sdXX
```
(change sdXX accordingly)

---

### Post by warrior_juggalo on 2010-03-16
How do i find witch one my networking hard drive is?, I thought the whole "sdb1" type deal was only for internal hard drives?

---

### Post by warrior_juggalo on 2010-03-17
Hello?

---

### Post by soltanis on 2010-03-17
How do you access the drive? Is it an externally connected drive, or is it, as your title suggests, connected to a remote server that you access with some protocol (like Amazon S3, FTP, etc)?

---

### Post by warrior_juggalo on 2010-03-17
External, Plug's into the router.

---

### Post by pbpersson on 2010-03-17
If you have the external drive mounted on your desktop you should be able to check it by right-clicking and doing "properties" or you could use the command line solution previously mentioned.

For instance, if I had used smb4k to mount the "MyData" share from machine 192.168.0.132, the commands would be:

```
cd smb4k/192.168.0.132
sudo df MyData
```

and the output would be:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
//192.168.0.132/MyData
                     965040612 850065208 114975404  89% /home/phil/smb4k/192.168.0.132/MyData
```

however, your actual results will vary

---

