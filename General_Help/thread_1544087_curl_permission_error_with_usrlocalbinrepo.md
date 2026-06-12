---
title: "curl permission error with /usr/local/bin/repo"
date: 2010-08-02
forum: General Help
---

### Post by ic3man5 on 2010-08-02
I'm trying to grab "repo" using curl and put it into /usr/local/bin/ but I can't seem to figure out why I'm getting a permission error:

```
$ sudo curl https://android.git.kernel.org/repo > /usr/local/bin/repo
bash: /usr/local/bin/repo: Permission denied

``````
$ ls -al /usr/local/bin/
total 8
drwxr-xr-x  2 root root 4096 2010-04-29 08:17 .
drwxr-xr-x 10 root root 4096 2010-04-29 08:17 ..

``````
$ ls -al /usr/local/
total 40
drwxr-xr-x 10 root root 4096 2010-04-29 08:17 .
drwxr-xr-x 11 root root 4096 2010-08-02 01:56 ..
drwxr-xr-x  2 root root 4096 2010-04-29 08:17 bin
drwxr-xr-x  2 root root 4096 2010-04-29 08:17 etc
drwxr-xr-x  2 root root 4096 2010-04-29 08:17 games
drwxr-xr-x  2 root root 4096 2010-04-29 08:17 include
drwxr-xr-x  3 root root 4096 2010-04-29 08:18 lib
lrwxrwxrwx  1 root root    9 2010-07-09 00:37 man -> share/man
drwxr-xr-x  2 root root 4096 2010-04-29 08:17 sbin
drwxr-xr-x  8 root root 4096 2010-07-09 00:58 share
drwxr-xr-x  2 root root 4096 2010-04-29 08:17 src

``````
$ uname -a
Linux david-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

```This is how I fixed it:
```
$ mv repo /usr/local/bin/
$ sudo chown root:root /usr/local/bin/repo
$ sudo chmod 755 /usr/local/bin/repo

```I'd still like to know why the curl method didn't work though.

---

### Post by andrewc6l on 2010-08-02
When you ran
```
$ sudo curl https://android.git.kernel.org/repo > /usr/local/bin/repo
```

you were running bash as yourself, and curl as root. The > redirect is bash behaviour, not curl behaviour - and the owner of the bash process (you) didn't have rights to write to /usr/local/bin/repo.

Here's a little article that describes it:

[http://notfaq.wordpress.com/2007/09/26/unixlinux-redirect-output-as-sudo/](http://notfaq.wordpress.com/2007/09/26/unixlinux-redirect-output-as-sudo/)

---

