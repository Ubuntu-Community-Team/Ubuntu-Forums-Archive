---
title: "/var/www - 403 .. chown/chmod doesn't help."
date: 2009-08-29
forum: General Help
---

### Post by credobyte on 2009-08-29
I don't know why but I can't seem to find a way to fix this issue .. 
By default, files were owned by root and had the same permissions as you see below. I tried to chown this folder, I tried to chmod directory and a few separate files ( you'll see the differences in the list of files I have there ) .. none of these things helped. I still get 403 ( Forbidden ) :(

Any ideas ?

```
dainis@sndpc:/var$ ls -l | grep www
drwxr-xr-x  3 dainis dainis 4096 2009-08-30 00:48 www
dainis@sndpc:/var$ cd www
dainis@sndpc:/var/www$ ls -l
total 8
drwx------ 5 dainis dainis 4096 2009-08-30 00:48 exchange
-rw-r--r-- 1 dainis dainis   45 2009-08-30 00:45 index.html
dainis@sndpc:/var/www$ cd exchange
dainis@sndpc:/var/www/exchange$ ls -l
total 44
drwx------ 2 dainis dainis 4096 2009-08-30 00:48 content
-rwx------ 1 dainis dainis 1592 2009-08-26 15:00 exchange.php
-rwx------ 1 dainis dainis  310 2009-08-25 06:44 getdata.php
drwx------ 2 dainis dainis 4096 2009-08-30 00:48 images
-rwxr-xr-x 1 dainis dainis 1428 2009-08-25 06:44 index.php
-rwx------ 1 dainis dainis 1750 2009-08-25 06:44 loader.js
-rwx------ 1 dainis dainis 1291 2009-08-25 06:44 menu.css
-rwx------ 1 dainis dainis 2471 2009-08-26 14:34 style.css
-rwx------ 1 dainis dainis 2442 2009-08-25 09:27 style_ie.css
drwx------ 2 dainis dainis 4096 2009-08-30 00:48 system
-rwx------ 1 dainis dainis 3305 2009-08-26 14:47 verify.php

```

---

### Post by scragar on 2009-08-29
```
chmod -R a+rx /var/www
```
That will get rid of your 403 errors, it's far from secure though.

---

### Post by Kewley on 2009-08-29
Edit: NVM, scragar posted first :P.

---

### Post by credobyte on 2009-08-29
> **scragar said:**
> ```
chmod -R a+rx /var/www
```That will get rid of your 403 errors, it's far from secure though.

Thank you. Regarding security - it's an offline workstation :)

---

### Post by scragar on 2009-08-29
I think by default the files belong to the user http, so it might be worth switching file ownership back and removing some file perms if it has to go public for some reason:
```
sudo chown http:http -R /var/www
sudo chmod -R 0700 /var/www

```I don't know if the sudo is needed for the first one, it might be though, I remember having problems giving perms to root before now...

---

### Post by credobyte on 2009-08-29
> **scragar said:**
> I think by default the files belong to the user http, so it might be worth switching file ownership back and removing some file perms if it has to go public for some reason:
```
sudo chown http:http -R /var/www
sudo chmod -R 0700 /var/www

```I don't know if the sudo is needed for the first one, it might be though, I remember having problems giving perms to root before now...

```
chown: invalid user: `http:http'
```

Gone missing :-k

---

### Post by scragar on 2009-08-29
> **credobyte said:**
> ```
chown: invalid user: `http:http'
```

Gone missing :-k

erm, http is the user on arch, I don't have an ubuntu pc anymore so I can't check what it'd be. sorry, looks like you're either going to just have to keep it out of nasty peoples way or wait for someone who does know to come along and edit my line.

---

