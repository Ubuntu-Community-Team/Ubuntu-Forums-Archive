---
title: "Sbackup / two questions"
date: 2009-11-14
forum: General Help
---

### Post by Ma55imo1973 on 2009-11-14
Hi all, I installed Ubuntu 8.04 Hardy Heron during last summer and I'm happy of the OS. Since September I use Sbackup in order to back the data up and I always did it with success thru the recommended settings. Until 3 weekg ago (last backup with Sbackup) the directory size was 3.7 GB and it could easily put on a 4.7 GB DVD. 

3 weeks ago I expanded the filesystem partition from 60 GB to 130 GB and now I find that the Sbackup directory size is 7.9 GB. Could it be due to the extension of the filesystem partition ? 

If not what could that be the reason ? And if so, instead, what directory should I backup in orderi to have a system always ready to be restored ? In the default settings directories /var, /usr/local, /etc and /home are suggested an I always followed the advice. 

Last question: if you replied you probably know Sbackup better than me. Do you know if Sbackup can be used to restore /home and the other data when I get to Ubuntu 9.04 or 9.10 ? Many thanks !

Massimo

---

### Post by paxmark1 on 2009-12-08
Last first.  Yes, sbackup should work swimmingly to restore /home.

That is it's greatest strength.  

However.  If you are have your partitions and system laid out with /  
/usr and other things on a different partitions, then you will not have to reinstall /home.  You just back it up prior to the upgrade or reinstall.  I have never had my /home degraded or lost in an upgrade or reinstall yet.  (I still back it up prior however)

For your first questions.  1.  Are you doing a full backup each time or are you doing sequential backups or diffs?  If you back it up sequentially each time, it gets progressively larger.  

I am looking up sbackup  because it has recently been getting stuck.  When it gets done backing up, the sbackup window will not disappear, even after a kill-9 of the process.  36 hours now.  It will minimize.  

It is a project that does not have a lot of enduring effort.  

peace, mark

---

