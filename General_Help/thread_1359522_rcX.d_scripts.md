---
title: "rcX.d scripts"
date: 2009-12-19
forum: General Help
---

### Post by testmod on 2009-12-19
I am currently trying to get a script to run at shutdown and restart that clears the contents of a given folder (ex: /home/USERNAME/.macromedia/Flash_Player/#SharedObjects)

Towards this end I have created a file clear-flash-cookies in /etc/init.d as follows:

```
#! /bin/bash
rm -f -r /home/USERNAME/.macromedia/Flash_Player/#SharedObjects/*
```I then created symbolic links as follows:
sudo ln -s /etc/init.d/clear-flash-cookies /etc/rc0.d/S00clear-flash-cookies
sudo ln -s /etc/init.d/clear-flash-cookies /etc/rc6.d/S00clear-flash-cookies


In my mind, this will run the scripts during shutdown and restart sequences.  This however is not happening.  What am I missing?

thanks

---

### Post by Brandon Williams on 2009-12-19
Two things come to mind.

First, double check ownership and permissons on the file in /etc/init.d/. You've probably already done that, but it never hurts looking one more time.

Second, all of the documentation I see on the net ([for example](http://www.debian-administration.org/articles/212)) indicates that the numbers in the link names should be from 01-99, but you used 00. I doubt this is it, but it won't hurt to try it with 01 instead.

---

### Post by testmod on 2009-12-19
Thanks, but it didn't work.

The script in /etc/init.d as well as the symbolic links are owned by root and root has read-write permission.

I changed the symbolic links to S01 and still not work.


very confusing..

---

