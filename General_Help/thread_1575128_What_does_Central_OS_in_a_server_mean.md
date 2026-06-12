---
title: "What does Central OS in a server mean???"
date: 2010-09-15
forum: General Help
---

### Post by shujathm4 on 2010-09-15
**What does Central OS in a server mean???**

---

### Post by lukeiamyourfather on 2010-09-15
Can you give the context?

---

### Post by shujathm4 on 2010-09-15
I mean, I asked my cutomer i see unix running on your server and he was asking me to enter linux commnads into it, i said will that accept, he said he has Cent oOS running on the server with red hat linux, It should mean multiple OS and not central OS, what exactly is this,I am quite new to linux, so plz help. thanks.

---

### Post by adit on 2010-09-15
I think you mean centos.
Centos is a linux distribution like ubuntu

---

### Post by shujathm4 on 2010-09-15
Thanks, but how is that possible i see Unix on the monitor with prompt as Unix? and the customer says linux running and I also enteerd linix commnads? does Linux commnads work in Unix or vice versa?

---

### Post by adit on 2010-09-15
There is no such thing as "Unix operating system" in 2010.  Today we have Unix-like operating systems both proprietary and free.

Free Unix-like:
1) Minix
2) Linux
3) FreeBSD
4) NetBSD
5) OpenBSD
6) OpenSolaris

Proprietary Unix-like:
1) Mac OS x
2) AIX
3) OpenServer
4) HP/UX
Linux is one of a member of these Unix-like operating systems.  Most of the above operating systems use bash shell.  That is why same command works in all these operating systems.

---

### Post by shujathm4 on 2010-09-15
That was a great reply thank you.

---

### Post by endotherm on 2010-09-15
I believe that if you type 'uname -a' at a terminal, you can check your kernel and info about your distro base:
```
$ uname -a
Linux Lucid 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux
```

---

### Post by lukeiamyourfather on 2010-09-15
What they all said. :)

[http://en.wikipedia.org/wiki/Unix](http://en.wikipedia.org/wiki/Unix)
[http://en.wikipedia.org/wiki/CentOS](http://en.wikipedia.org/wiki/CentOS)

---

