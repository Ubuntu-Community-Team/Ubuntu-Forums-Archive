---
title: "partitions"
date: 2010-09-07
forum: General Help
---

### Post by Makosz on 2010-09-07
It seems that I have seven partitions on my laptop while only 3 OS, I want to get format unnecessary partitions so it looks cleaner and there will be no future confusion if i need to reinstall anything for a reason. I have BackTrack 4, Ubuntu, and Windows 7. For some reason there are 2 partitions for Ubuntu one says Ubuntu 9.10 and other Ubuntu 10.04. Could you tell me how to do it in both the bash and the bash command line?

Thank you!!!

---

### Post by Sef on 2010-09-07
Let's see the partitions first.

Copy and paste this command in your Terminal (Applications > Accessories > Terminal):

```
sudo fdisk -l
```

Then copy and paste the results here.

---

### Post by Makosz on 2010-09-07
It says i Have 3 Linux OS while I only have Ubuntu 10.04 and Backtrack 4. Not sure where I saw that one of the partitions is Ubuntu 9.10. 

```
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       20315   147777078+   7  HPFS/NTFS
/dev/sda4           20316       38913   149388435    5  Extended
/dev/sda5           38589       38891     2433816   83  Linux
/dev/sda6           38892       38913      176683+  82  Linux swap / Solaris
/dev/sda7           20316       36118   126937534+  83  Linux
/dev/sda8           37842       38588     6000246   82  Linux swap / Solaris
/dev/sda9           36119       37763    13213431   83  Linux
/dev/sda10          37764       37841      626503+  82  Linux swap / Solaris

```

---

### Post by garvinrick4 on 2010-09-07
you have 
1 Dells utility
2 boot partiition
3 windows
4 extended partition (house for linux partitions)
5 linux
7 linux
9 linux
a swap for each linux.

You have 4 partitions 1 Windows and 3 linux

The first 4 are all Primary and fine need them all.
Of the 3 Linux in logical partitions are fine which ones do you not want.
sda5,sda7 or sda9.
Let Sef know which you are using.

---

### Post by Makosz on 2010-09-07
Since I installed Ubuntu 9.04 and upgraded to 10.04 before installing Bcktrack I am guessing sda9 is Backtrack and sda5 is Ubuntu 9.10. Where can i check to make sure of that?

If I remove Windows at one point can I format the 1st 4 partitions too or do i have to leave one because the laptop needs it to function?

---

### Post by srs5694 on 2010-09-07
Please don't post the same question to multiple forums. You posted the same question [here.](http://ubuntuforums.org/showthread.php?t=1569591)

---

