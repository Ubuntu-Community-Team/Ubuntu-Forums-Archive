---
title: "console-kit-daemon 64 threads predefined - why"
date: 2010-02-24
forum: General Help
---

### Post by rnerwein on 2010-02-24
hi
i'm running:
Distributor ID: Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:   karmic
2.6.31-16-generic
amd64

i hope this the right section for this question.
just for interesting. why does the console-kit-daemon starts 64 threads 
form startup on. i use threads, very mostely only on demand and then only 
for high performance reasons situations i'll create a predefined number of 
threads ( depends on the application ). but i see no reason for
the console-kit-daemon to do this ( may be i don't know the challenge of this
processc )

/usr/sbin/console-kit-daemon - running 64 threads
parent process is pid 1 - init
thread creater in:
    restart_syscall(<... resuming interrupted call ...>
thread ( number 1 to 64 ) in:
    ioctl(11, VIDIOC_S_COMP or VT_WAITACTIVE
    
thanks for any explanation
ciao

---

### Post by lavinog on 2010-02-24
This has come up many times in the past.
If I understand correctly, the multiple instances are used to keep session info for different users.

Some users thought it creates a performance hit, but I have yet to see any evidence.

Edit: it seems to be associated with fast-user-switching.

---

### Post by lavinog on 2010-02-24
Some info about the subject:
[https://bugs.freedesktop.org/show_bug.cgi?id=17720](https://bugs.freedesktop.org/show_bug.cgi?id=17720)

---

### Post by rnerwein on 2010-02-24
hi
i'll close that post. found in the net a good explanation ( even the source code ) of this process.
p.s. i don't thougt that this is a performance problem.
ciao

---

