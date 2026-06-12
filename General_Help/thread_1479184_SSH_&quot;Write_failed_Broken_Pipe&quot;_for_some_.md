---
title: "SSH &quot;Write failed: Broken Pipe&quot; for some users"
date: 2010-05-10
forum: General Help
---

### Post by blueyelabs on 2010-05-10
Hi All,

I am having a truly bizarre problem when trying to set up my sheeva plug as a backup server. I have four users (one for each member of my family) that I want to give permission to ssh in (well, sftp in but they're essentially the same) and backup to an external harddrive.

My user works perfectly well and has done since I got the plug. So does a transmission user I set up to run the transmission daemon. With the other three users, however, I get the following error after SSH asks for the user's password:
```

Write failed: Broken pipe

```

This happens whether I try locally or over my network. I haven't been able to find a solution to it at all. I've made sure that /bin/bash was set as the shell and that the home directory is writeable with the correct permissions (ls -al /home):
```

drwxr-xr-x  7 root         root         4096 Dec 21 19:25 .
drwxr-xr-x 21 root         root         4096 Dec 17 19:27 ..
drwxr-xr-x  7 gideon       gideon       4096 Apr 28 11:03 gideon
drwxr-xr-x  3 gill         gill         4096 May  8 13:02 gill
drwxr-xr-x  3 indi         indi         4096 May  8 13:02 indi
drwxr-xr-x  3 rory         rory         4096 May  8 13:02 rory
drwxr-xr-x  4 transmission transmission 4096 Dec 18 01:05 transmission

```

Does anyone know what could be going wrong? The alternative for me would be to use netatalk and AFP but the problem is that there is no native support for AFP and so things like déja dup backup may not be able to mount the afp drive... Je sais pas.

Thanks in advance.

---

### Post by volobiz on 2010-06-30
I'm getting this error now if I have a stale SSH connection that I leave alone. It disconnects the idle SSH connection, but not without first generating this error message. I have no idea what it is.

---

### Post by blueyelabs on 2010-06-30
Check user groups and stuff like that. I removed an "sftp" group that I had created and it fixed the problem.

---

### Post by bithead on 2010-08-18
Try this thread:
[https://bbs.archlinux.org/viewtopic.php?id=97003](https://bbs.archlinux.org/viewtopic.php?id=97003)

---

### Post by lpwaqas on 2011-09-02
This is very old problem for me; Every time I reinstall my system I have to add the line below to my  /etc/ssh/ssh_config to avoid “Write failed: Broken pipe” issue.

ServerAliveInterval 120
OR
ClientAliveInterval 15

---

### Post by alazyrabbit on 2011-10-07
To make a complementary, since the network is unstable, I wrote a shell script to automatically restart the SSH session.
[http://nextspaceship.com/2011/09/how-to-solve-broken-pipe-message-in-ssh-session/](http://nextspaceship.com/2011/09/how-to-solve-broken-pipe-message-in-ssh-session/)

---

