---
title: "unattended backup on ubuntu"
date: 2012-10-03
forum: General Help
---

### Post by hhaydoura on 2012-10-03
Hey people:) I've been asked from my boss to complete a task about automated (un-attended backup.. he wants me to login from a client pc and connect to the server and do this job,  can anyone help me in this??

---

### Post by 2F4U on 2012-10-03
There is a lot of backup software available, this site gives a short overview of the options

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by Prospero2006 on 2012-10-03
> **hhaydoura said:**
> Hey people:) I've been asked from my boss to complete a task about automated (un-attended backup.. he wants me to login from a client pc and connect to the server and do this job,  can anyone help me in this??

I manage a computer lab in a public school and for my computer lab I find rsync to be very useful. You can configure it to run every hour or so via cron. If you accidentally wipe out a folder on drive a, for example, it will not be erased on drive b (the backup). If, however, you add a folder to drive a it will be added to drive b. 
(You can tell it to do a complete sync and delete the missing folders, but I only do this once a year.)

I'll check back here to see what others are using. This is a good topic for me. 

Good luck.

---

### Post by hhaydoura on 2012-10-03
lol i'm talking about server backup from a random pc and thats whats confusing me, and i need to know the steps to complete this

---

### Post by muteXe on 2012-10-03
yes, you need rsync.
[http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)
[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

---

