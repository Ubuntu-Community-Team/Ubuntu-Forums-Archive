---
title: "`ls -l | sort` do not work"
date: 2009-11-27
forum: General Help
---

### Post by andrejanubis1 on 2009-11-27
I would like to sort files and folders in dictionary order but I am not happy with the next result:
```
-rwxr-xr-x    1 mcqstk   grpqa          4126 May 29 2008  star
-rwxr-xr-x    1 mcqstk   grpqa          3758 May 29 2008  stop
-rwxr-xr-x    1 mcqstk   grpqa          2052 May 29 2008  node
-rwxr-xr-x    1 mcqstk   grpqa          1958 May 29 2008  laun
-rwxr-xr-x    1 mcqstk   grpqa          1946 May 29 2008  regi
```I have tried more examples like: `**ls -l | sort -dr**` and `**ls -l | sort -d -k 9**` but is not good either. It would be great if files and folders wold be together. How can I fixed that? Please help...Thank you.

---

### Post by emigrant on 2009-11-27
hows this:

```
ls -l | sort -k8
```

---

### Post by andrejanubis1 on 2009-11-27
No, it is not in alphabet neither folders and files together. Thanx any way.

---

### Post by dcstar on 2009-11-28
> **andrejanubis1 said:**
> I would like to sort files and folders in dictionary order but I am not happy with the next result:
```
-rwxr-xr-x    1 mcqstk   grpqa          4126 May 29 2008  star
-rwxr-xr-x    1 mcqstk   grpqa          3758 May 29 2008  stop
-rwxr-xr-x    1 mcqstk   grpqa          2052 May 29 2008  node
-rwxr-xr-x    1 mcqstk   grpqa          1958 May 29 2008  laun
-rwxr-xr-x    1 mcqstk   grpqa          1946 May 29 2008  regi
```I have tried more examples like: `**ls -l | sort -dr**` and `**ls -l | sort -d -k 9**` but is not good either. It would be great if files and folders wold be together. How can I fixed that? Please help...Thank you.

"ls -l" sorts in alphabetical name order by default.

---

### Post by bodhi.zazen on 2009-11-28
Are you running some custom shell or custom ls ?

> ls -l
-rw-r--r-- 1 bodhi bodhi 0 2009-11-27 22:48 laun
-rw-r--r-- 1 bodhi bodhi 0 2009-11-27 22:48 node
-rw-r--r-- 1 bodhi bodhi 0 2009-11-27 22:48 regi
-rw-r--r-- 1 bodhi bodhi 0 2009-11-27 22:48 star
-rw-r--r-- 1 bodhi bodhi 0 2009-11-27 22:48 stop

ls -l | sort
-rw-r--r-- 1 bodhi bodhi 0 2009-11-27 22:48 laun
-rw-r--r-- 1 bodhi bodhi 0 2009-11-27 22:48 node
-rw-r--r-- 1 bodhi bodhi 0 2009-11-27 22:48 regi
-rw-r--r-- 1 bodhi bodhi 0 2009-11-27 22:48 star
-rw-r--r-- 1 bodhi bodhi 0 2009-11-27 22:48 stop

---

### Post by andrejanubis1 on 2009-11-30
> **dcstar said:**
> "ls -l" sorts in alphabetical name order by default.
In case of `**ls -l**`I get: ```
drwx--x--x   2 andrej   usr            4096 Jan 06 2009  Mail
-rwxr-xr-x   1 andrej   usr              36 Jul 25 10:25 cont
-rw-r--r--   1 andrej   usr           22030 Jul 08 13:27 geiaLog
-rwxr--r--   1 andrej   usr             550 Jul 08 13:35 manPage
-rwxrwxrwx   1 andrej   usr             258 Sep 03 09:00 shell.bsh
drwxr-xr-x   3 andrej   usr            4096 Sep 09 14:28 zdaj

```> **bodhi.zazen said:**
> Are you running some custom shell or custom ls ?

This I am not sure, how can I check that?  
Thanks all for ideas !

---

### Post by emigrant on 2009-11-30
> **andrejanubis1 said:**
> This I am not sure, how can I check that?  


you edited your .bashrc?
check/post output:

```
less ~/.bashrc | grep alias
```

---

### Post by andrejanubis1 on 2009-11-30
I do not remember that I did edited .bashrc, but someone else may did, harde for me to check. I hardly believe it is so much problem to sort by folders an alphabet in this two groups.
```
*******************************************************************************
*                                                                             *
*                                                                             *
*  Welcome to AIX Version 5.3!                                                *
*                                                                             *
*                                                                             *
*  Please see the README file in /usr/lpp/bos for information pertinent to    *
*  this release of the AIX Operating System.                                  *
*                                                                             *
*                                                                             *
*******************************************************************************
-bash-3.00$ less ~/.bashrc | grep alias
-bash: less: command not found

```Thank you for help

---

### Post by jespdj on 2009-11-30
> Welcome to AIX Version 5.3!
You're not running Linux - you are running AIX, which is IBM's implementation of Unix.

Why are you asking your question in a forum about Ubuntu Linux?

---

### Post by Kevbert on 2009-11-30
Just tried this on my /home folder on 9.04 64 bit and have to use
```
$ ls -l | sort -k8

```
so that I get everything in alphanumeric order. If I use
```
ls -l | sort
```
nothing is in order.

---

### Post by andrejanubis1 on 2009-11-30
How could I fist sort by 1 and then by 2 column as seen below:```
1                                                        2
-rwxrwxrwx   1 andrej   usr             258 Sep 03 09:00 shell.bsh
drwxr-xr-x   3 andrej   usr            4096 Sep 09 14:28 zdaj
```?

---

### Post by andrejanubis1 on 2009-12-02
> **andrejanubis1 said:**
> How could I fist sort by 1 and then by 2 column as seen below:```
1                                                        2
-rwxrwxrwx   1 andrej   usr             258 Sep 03 09:00 shell.bsh
drwxr-xr-x   3 andrej   usr            4096 Sep 09 14:28 zdaj
```?
Is that can not be done?

---

### Post by john newbuntu on 2009-12-02
ls --group-directories-first -l

---

### Post by andrejanubis1 on 2009-12-03
Thank you all for help.

---

