---
title: "sBackup: no backups found in the target directory."
date: 2011-07-09
forum: General Help
---

### Post by BulgarianBoy on 2011-07-09
I want to backup some files and I followed a tutorial on how to use sbackup and simple restore but when I go to simple restore it says the there are "no backups found in the target directory"
Then I found a post on the forums with the same problem. In the post he talked about two lines of code that are below and he said based on the output I can tell you what to do next. I don't know what to do next because there was nothing after that. And I think I am missing flist. Help please.


code:  ls -l /var

output:
total 52
drwxr-x---  3 root root  4096 2011-07-09 20:05 backup
drwxr-xr-x  2 root root  4096 2011-07-09 01:10 backups
drwxr-xr-x 19 root root  4096 2010-12-04 17:53 cache
drwxrwxrwt  2 root root  4096 2011-01-30 07:35 crash
drwxr-xr-x  2 root root  4096 2010-08-16 02:48 games
drwxr-xr-x 68 root root  4096 2011-07-08 23:33 lib
drwxrwsr-x  2 root staff 4096 2010-04-23 03:11 local
drwxrwxrwt  3 root root    80 2011-07-09 20:05 lock
drwxr-xr-x 17 root root  4096 2011-07-09 17:37 log
drwxrwsr-x  2 root mail  4096 2010-08-16 02:32 mail
drwxr-xr-x  2 root root  4096 2010-08-16 02:32 opt
drwxrwxrwt  3 root root  4096 2011-07-08 16:25 parallels
drwxr-xr-x 18 root root   880 2011-07-09 19:47 run
drwxr-xr-x  9 root root  4096 2010-10-22 21:23 spool
drwxrwxrwt  3 root root  4096 2011-07-09 20:23 tmp

second code: sudo ls -l /var/backup
second output:
total 4
drwxr-x--- 2 root root 4096 2011-07-09 20:05 2011-07-09_20.05.24.756358.moris-laptop.ful

---

### Post by wildmanne39 on 2011-07-09
Hi, I had problems with sbackup also I ended up switching to Deja Dup. It has work good so far.

---

### Post by BulgarianBoy on 2011-07-10
Does let me do custom like sBackup?

---

### Post by wildmanne39 on 2011-07-10
> **BulgarianBoy said:**
> Does let me do custom like sBackup?
Hi, yes you can set it to backup just the folders you want it too.

---

### Post by BulgarianBoy on 2011-07-10
do you think you can write me a quick tutorial on how to use it? and what the different file types are?

---

### Post by wildmanne39 on 2011-07-10
> **BulgarianBoy said:**
> do you think you can write me a quick tutorial on how to use it? and what the different file types are?Hi, it comes with a help file and also an option to get help online, I personally did not read the help file it was easy to use.

---

### Post by BulgarianBoy on 2011-07-10
I am a newb. Didn't see the help file. Thank you.

---

### Post by BulgarianBoy on 2011-07-10
One more question. What files should I include in the backup?

---

### Post by wildmanne39 on 2011-07-10
> **BulgarianBoy said:**
> One more question. What files should I include in the backup?Hi, this link will answer your question and would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by BulgarianBoy on 2011-07-10
Thank you again.

---

