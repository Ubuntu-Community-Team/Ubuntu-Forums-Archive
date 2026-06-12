---
title: "unzip db archieve"
date: 2009-11-06
forum: General Help
---

### Post by terbor on 2009-11-06
I downloaded my db for backup via phpmyadmin.  I am not trying to upload it and phpmyadmin give me an error so I am trying to extract it on my desktop and I am getting this error. Ubunut 8.04 Hardy

Here is the error:
```
robert@robert-desktop:~/Desktop$ unzip modirac.csv.zip 
Archive:  modirac.csv.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of modirac.csv.zip or
        modirac.csv.zip.zip, and cannot find modirac.csv.zip.ZIP, period.
robert@robert-desktop:~/Desktop$ sudo unzip modirac.csv.zip
```

Thanks for any assistance

---

### Post by Giblet5 on 2009-11-06
Hmm. It does the same thing on my install of phpmyadmin.

A bug in phpmyadmin!

Choosing bzip2 works.


This is listed as bug 495767 on [linux.debian.bugs.list]("http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/468fcc54f4a84faa").

---

### Post by BitJunkie on 2009-11-06
What's the output of ```
file modirac.csv.zip
```

---

### Post by ManiacDan on 2009-11-06
What's inside the file?  Do:
> head modirac.csv.zip 

If that returns readable text, it's just NAMED zip, it's not actually zipped.

-Dan

---

### Post by terbor on 2009-11-06
```
robert@robert-desktop:~/Desktop$ file modirac.csv.zip
modirac.csv.zip: ASCII text

```

```
robert@robert-desktop:~/Desktop$ head modirac.csv.zip
<br />
<b>Fatal error</b>:  Allowed memory size of 134217728 bytes exhausted (tried to allocate 126877736 bytes) in <b>/var/www/phpmyadmin/export.php</b> on line <b>132</b><br />
```

I am guessing the file was too big to begin with ....  I just wish I would have gotten an error from phpmyadmin when I downloaded the file ...

---

### Post by Giblet5 on 2009-11-06
More research needed... That bug report is wrong.

I just verified that gzip and bzip2 both work. "zipped" does not work. It generates an error that it required too much memory (probably running into a phpmyadmin ulimit...)

---

### Post by ManiacDan on 2009-11-06
That's a PHP fatal error, you can tell because it's outputting HTML tags.  PHPMyAdmin ran out of memory while attempting to dump, but because all output was redirected into the file, you didn't realize until now.  You should have checked the filesize to make sure it was bigger than the 500 bytes it probably is right now.  

If you don't have an existing backup, you've lost everything.  Sorry.

I ALWAYS back up my MySQL databases using the command line tool mysqldump.  Check the MySQL manual or the man page for more. 

-Dan

---

### Post by Giblet5 on 2009-11-06
> **ManiacDan said:**
> That's a PHP fatal error, you can tell because it's outputting HTML tags.  PHPMyAdmin ran out of memory while attempting to dump, but because all output was redirected into the file, you didn't realize until now.  You should have checked the filesize to make sure it was bigger than the 500 bytes it probably is right now.  

If you don't have an existing backup, you've lost everything.  Sorry.

I ALWAYS back up my MySQL databases using the command line tool mysqldump.  Check the MySQL manual or the man page for more. 

-Dan

+1

I do mysqldump, then I shut down the server and back up the data files every night.

The latter is a 20-second restore... Handy when you type DROP instead of USE.

---

### Post by terbor on 2009-11-06
yeah I tried using ctrl - z after I hit drop database .... it didnt work:KS

I guess I kind of knew this answer, I was just hoping that maybe someone knew of a secret that could help me recover it.

thanks for replying all ....

---

### Post by ManiacDan on 2009-11-06
Not unless you've backed up the db, have a hard drive restore set up, are using a mac with time machine, or have a slave database that's been recently disconnected, no.  This is why you should make a user for yourself without the DROP permission and work in that.  It's the same reason we don't run in root, you get stopped from doing stupid things.

-Dan

---

