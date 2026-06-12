---
title: "folders in my home directory whose name begins with &quot;.fr-&quot;"
date: 2010-03-24
forum: General Help
---

### Post by desconocido on 2010-03-24
Does anyone know what software creates them? Can I safely delete them?

Here is an example name:
.fr-AYuDW9

Thanks

---

### Post by chaanakya_chiraag on 2010-03-24
Can you open up a terminal (Applications->Accessories->Terminal) and post the output of the following output:
```
cd .fr-AYuDW9
ls -l
```
That should enlighten us a little :)
- Chiraag

---

### Post by desconocido on 2010-03-26
Hi,

```
bob@faustino:~$ cd .fr-AYuDW9
bob@faustino:~/.fr-AYuDW9$ ls -l
total 4
drwxr-xr-x 5 bob bob 4096 2010-03-17 18:09 wordpress
bob@faustino:~/.fr-AYuDW9$ ls -l wordpress
total 292
-rw-r--r-- 1 bob bob   397 2008-05-25 22:33 index.php
-rw-r--r-- 1 bob bob 15410 2008-12-06 08:47 license.txt
-rw-r--r-- 1 bob bob  7644 2010-02-13 20:35 readme.html
drwxr-xr-x 8 bob bob  4096 2010-03-17 18:09 wp-admin
-rw-r--r-- 1 bob bob 40400 2009-10-25 11:32 wp-app.php
-rw-r--r-- 1 bob bob   220 2008-10-14 08:22 wp-atom.php
-rw-r--r-- 1 bob bob   274 2008-05-25 17:50 wp-blog-header.php
-rw-r--r-- 1 bob bob  3928 2010-01-07 20:38 wp-comments-post.php
-rw-r--r-- 1 bob bob   238 2008-10-14 08:22 wp-commentsrss2.php
-rw-r--r-- 1 bob bob  2616 2009-12-08 20:59 wp-config-sample.php
drwxr-xr-x 4 bob bob  4096 2010-03-17 18:09 wp-content
-rw-r--r-- 1 bob bob  1253 2009-08-16 06:59 wp-cron.php
-rw-r--r-- 1 bob bob   220 2008-10-14 08:22 wp-feed.php
drwxr-xr-x 6 bob bob  4096 2010-03-17 18:09 wp-includes
-rw-r--r-- 1 bob bob  1946 2009-05-05 21:43 wp-links-opml.php
-rw-r--r-- 1 bob bob  2341 2009-05-20 18:32 wp-load.php
-rw-r--r-- 1 bob bob 22721 2009-12-14 23:09 wp-login.php
-rw-r--r-- 1 bob bob  7578 2009-09-18 22:43 wp-mail.php
-rw-r--r-- 1 bob bob   487 2009-04-20 23:50 wp-pass.php
-rw-r--r-- 1 bob bob   218 2008-10-14 08:22 wp-rdf.php
-rw-r--r-- 1 bob bob   316 2008-05-25 17:50 wp-register.php
-rw-r--r-- 1 bob bob   220 2008-10-14 08:22 wp-rss2.php
-rw-r--r-- 1 bob bob   218 2008-10-14 08:22 wp-rss.php
-rw-r--r-- 1 bob bob 23097 2009-12-14 01:38 wp-settings.php
-rw-r--r-- 1 bob bob  3693 2009-11-26 12:29 wp-trackback.php
-rw-r--r-- 1 bob bob 93445 2009-12-01 09:14 xmlrpc.php
```

The other three .fr- folders, which I have deleted, contained files related to a program called "Processing". I have the Wordpress and Processing software elsewhere, where they should be. Just don't know what created these folders.

---

### Post by chaanakya_chiraag on 2010-03-26
I have a feeling WordPress created the folder to store its settings.

---

### Post by desconocido on 2010-03-29
> **chaanakya_chiraag said:**
> I have a feeling WordPress created the folder to store its settings.
No, I would recognise the settings files. I have not examined every subfolder, but it looks like a copy of the folder elsewhere that contains all the wordpress software.

---

### Post by chaanakya_chiraag on 2010-03-29
If you're implying that the WordPress program stores all of its settings inside the folder containing the software, I have a feeling that's wrong simply because no software ever does that (except for some global settings).  Every piece of software stores its settings on a per-user basis in the user's .AppData directory (Windows) or as a "dot-folder" in Linux.  Try moving all of these folders to .whatever[B].bak]/B] and start WordPress to see if anything changes.

---

### Post by desconocido on 2010-04-09
Another .fr- folder got created.

All it contained was a DEBIAN.readme file talking about Apache and php.

---

### Post by chaanakya_chiraag on 2010-04-11
Try moving it to .fr-whatever**.bak** and try doing whatever you normally do.  Does anything go wrong/get reset?

---

### Post by desconocido on 2010-04-27
> **chaanakya_chiraag said:**
> Try moving it to .fr-whatever**.bak** and try doing whatever you normally do.  Does anything go wrong/get reset?

Yep, nothing happened (I think).

Could it be a Firefox bug?

---

### Post by dino99 on 2010-04-27
it's a hidden index file, no more

if you want/need to make room and clean your system, there are 2 tools you can use:

- gconf-cleaner
- bleachbit: run it as admin but take the time to read and understand what you are selecting if you dont want to loose bookmarks, passwords ...

---

