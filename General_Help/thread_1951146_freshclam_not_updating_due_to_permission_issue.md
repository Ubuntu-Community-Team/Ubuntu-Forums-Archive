---
title: "freshclam not updating due to permission issue"
date: 2012-04-02
forum: General Help
---

### Post by antiartist on 2012-04-02
freshclam doesn't want to update the signature database due to a permissions problem with the logfile:

```
ERROR: Can't open /var/log/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/freshclam.log).

```

The permissions for the freshclam.log file are wide open:
```
tom@HouseMedia:~$ ls -al /var/log/
-rwxrwxrwx  1 clamav    clamav           0 2012-03-17 01:36 freshclam.log

```
And although this shouldn't be a problem, I check the parent folder as well:
```
tom@HouseMedia:~$ ls -ld /var/log/
drwxr-xr-x 18 root root 4096 2012-04-01 06:48 /var/log/

```

Help?

---

### Post by Bucky Ball on 2012-04-02
What release are you using?

---

### Post by dcstar on 2012-04-02
> **antiartist said:**
> freshclam doesn't want to update the signature database due to a permissions problem with the logfile:
.........
The permissions for the freshclam.log file are wide open:
```
tom@HouseMedia:~$ ls -al /var/log/
-rwxrwxrwx  1 clamav    clamav           0 2012-03-17 01:36 freshclam.log

```


Here is mine:

```
-rw-r----- 1 clamav adm  7797 2012-04-02 18:13 freshclam.log
```

---

### Post by antiartist on 2012-05-05
> **Bucky Ball said:**
> What release are you using?

Ubuntu Linux 10.04.2
ClamAV 0.96.5 (does that sound right? I downloaded it probably a month ago)

---

### Post by antiartist on 2012-08-07
<bump>

---

### Post by claracc on 2012-08-08
Have you changed group owner and permissions in the file?

As dcstar has pointed, fresclam.log group has to be adm, and permissions -rw-r-----

---

### Post by antiartist on 2012-08-11
> **claracc said:**
> Have you changed group owner and permissions in the file?

As dcstar has pointed, fresclam.log group has to be adm, and permissions -rw-r-----

Look like I fiddled some more after making my permissions post as it is now what dcstar suggested...

```
tom@HouseMedia:/var/log$ ls -l freshclam.log
-rw-r----- 1 clamav adm 0 2012-08-05 06:30 freshclam.log
```

---

### Post by claracc on 2012-08-11
So, if you run sudo freshclam in xterm, what do you obtain now ?

---

### Post by antiartist on 2012-08-12
Nothing has changed.  I still get the same error:

> ERROR: Can't open /var/log/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/freshclam.log).

---

### Post by claracc on 2012-08-12
I don't have freshclam.log file under /var/log/ but under /var/log/clamav/

> clara@clara1:/var/log/clamav$ ls -la
total 168
drwxr-xr-x  2 clamav clamav  4096 2012-08-05 08:09 .
drwxr-xr-x 18 root   root    4096 2012-08-12 08:23 ..
-rw-r-----  1 clamav adm    50729 2012-08-12 08:23 freshclam.log


---

### Post by antiartist on 2012-08-12
Interesting...I also have a log file there as well.  But permissions and owner/group are the same:
> tom@HouseMedia:/var/log/clamav$ ls -l freshclam.log
-rw-r----- 1 clamav adm 0 2012-06-20 13:31 freshclam.log

---

### Post by claracc on 2012-08-12
I would remove the freshclam.log file under /var/log/

---

### Post by antiartist on 2012-08-13
I changed the "updatelogfile=" line in freshclam.conf to /var/log/clamav.  That resolved the problem!!

Well, now I get:

> Update failed. Your network may be down or none of the mirrors listed in /etc/clamav/freshclam.conf is working. 

But that will be another thread ;)

thanks for the help!

---

