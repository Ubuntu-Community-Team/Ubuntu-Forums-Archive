---
title: "Can't save php files to /var/www"
date: 2010-06-20
forum: General Help
---

### Post by Timbothecat on 2010-06-20
Hi Guys.

I'm really hoping that someone here can help. I'm running Ubuntu 9.10 in a virtual machine and trying to do some work with php. I'm using Bluefish editor to create a very simple file that will show the date on a web page. The problem is that I try to save the file and get the following error:

Error opening file '/var/www/today.php': Permission denied.

Obviously it's a permissions issue. So I followed the instructions found in this post:

[http://ubuntuforums.org/archive/index.php/t-135530.html](http://ubuntuforums.org/archive/index.php/t-135530.html)

but alas, I keep getting the error.

Any help would be greatly appreciated.

All the best,

Tim.

---

### Post by NCLI on 2010-06-20
Could you please post the output of
```
ls -l /var
```

---

### Post by nathan726 on 2010-06-20
This should do the trick:
sudo chown  -R $USER:$USER /var/www

Alternatively, if you need to write to or edit a file, use  'gksudo gedit <filename>'.
If you need to do any moving/copying to  that area, use 'sudo mv'.

---

### Post by Timbothecat on 2010-06-20
NCLI, here's the output you were after:

[INDENT]drwxr-xr-x  2 root root  4096 2010-06-20 18:51 backups
drwxr-xr-x 23 root root  4096 2010-06-20 17:47 cache
drwxrwxrwt  2 root root  4096 2009-10-16 03:29 crash
drwxr-xr-x  2 root root  4096 2009-10-29 08:02 games
drwxr-xr-x 66 root root  4096 2010-06-20 18:29 lib
drwxrwsr-x  2 root staff 4096 2009-10-20 11:04 local
drwxrwxrwt  3 root root    60 2010-06-20 18:51 lock
drwxr-xr-x 18 root root  4096 2010-06-20 18:51 log
drwxrwsr-x  2 root mail  4096 2009-10-29 07:55 mail
drwxr-xr-x  2 root root  4096 2009-10-29 07:55 opt
drwxr-xr-x 18 root root   680 2010-06-20 18:37 run
drwxr-xr-x  6 root root  4096 2009-10-29 07:58 spool
drwxrwxrwt  3 root root  4096 2010-06-20 18:42 tmp
drwxr-xr-x  2 root root  4096 2010-03-07 16:12 www
[/INDENT]


Looking at that -and with my limited knowledge of Linux- it would appear that I don't have write access, is that right?

Nathan... I know that would work, but I was sort of hoping to use that as a last resort. 

Thanks for your responses guys, much appreciated.

Tim.

---

### Post by Timbothecat on 2010-06-20
Hi NCLI.

I've fixed the problem. What I had done was put a wildcard at the end of the command.

I had "chmod g+rw /var/www/*" which of course gave me access to any folders inside www. I took out the wildcard, and the rest -as they say- is history. Thank you so much for your post because I never would have seen the problem without it.

All the best,

Tim.

---

### Post by NCLI on 2010-06-20
Glad to hear it, remember to mark as solved :)

---

### Post by Timbothecat on 2010-06-20
I tried to do that but I couldn't see how mate. I'll keep looking though.

---

### Post by wojox on 2010-06-20
> **Timbothecat said:**
> I tried to do that but I couldn't see how mate. I'll keep looking though.

Up at the top under Thread Tools :p

---

### Post by Timbothecat on 2010-06-20
Found it... what a silly bunt. :oops::tongue:#-o

---

### Post by darenjoe on 2011-02-02
This was the help I needed. I am using bluefish and I was trying to find how to raise permissions for bluefish(if that is possible) rather than lower the folder permissions, but what ever. It worked. 
Daren

---

