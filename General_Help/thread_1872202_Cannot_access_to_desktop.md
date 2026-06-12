---
title: "Cannot access to desktop"
date: 2011-10-30
forum: General Help
---

### Post by telapo on 2011-10-30
Hi all, 
I cannot access to my desktop (Ubuntu 11.10 with both unity and gnome), I try to log in but the log windows just reload itself after I insert my password, which is the right password, this is not a problem about password. If I tried to log in after press Ctrl alt f1 I got: 
```
Mount of device (uid: 1016) not owned by requested user (uid: 1000)
Reading sb failed; rc=[-1]
Mount operation not permitted
To run a command as administrator...
```
My hard disk is divided in 4 partition (windows, ubuntu, swap and home), grub seems working fine, I don't know what to do, this is not a new installation or configuration, until yesterday everything was working fine, this morning I turn on the pc and it doesn't log in, I don't touch anything yesterday, just surf on the web and installed some updates but through the update manager nothing of experimental at all.
Help me! Please ;)

---

### Post by l3iggs on 2011-10-31
Same exact thing here. Wtf is going on? Anyone?

I can login via tty1 and none of my files are there (i.e. my encrypted home dir has not been mounted)

Then if I run:

$ ecryptfs-mount-private
Mount of device (uid: 0) not owned by requested user (uid: 1000)
Reading sb failed; rc = [-1]
Enter your login passphrase:
Mount of device (uid: 0) not owned by requested user (uid: 1000)
Reading sb failed; rc = [-1]
mount: Operation not permitted

---

### Post by telapo on 2011-11-01
I couldn't find any solution, so I mounted my partition from live cd, burned all the important data and then reinstalled ubuntu 11.10 erasing anything except the windows partition. I hope it doesn't happen again because is a really disappointing thing. I hope too you will be more lucky than me.

---

### Post by l3iggs on 2011-11-01
i suspect it was some software update that broke this. i have oneiric-security, oneiric-updates, oneiric-proposed, and oneiric-backports checked as update sources. did you have the same?

---

### Post by telapo on 2011-11-01
Yes, except for oneiric-proposed, but I had also other external sources, for example for the system monitor, the weather and others.

---

### Post by l3iggs on 2011-11-02
solved:

let's assume your username is 'user' then

```
$ sudo chown user:user /home/.ecryptfs/user/.Private
```

fixed the issue for me. no idea how my permissions got messed up.

---

### Post by telapo on 2011-11-02
**Great!!! **
For me it's too late, but I hope it will be useful for someone else who will experience the same problem!
I'm going to change the title of the thread.

---

### Post by cdq74cn24 on 2011-12-06
Thank You, Save my night !

I don't know how/why the permission gone.

---

