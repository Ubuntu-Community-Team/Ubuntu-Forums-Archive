---
title: "Ubuntu boot process, rc.local how??"
date: 2011-05-30
forum: General Help
---

### Post by northfly on 2011-05-30
looks from runlevel 2 to 5, the /init.d/rc.local is executed, if I put something I want to startup here I can have it.

But looks documents suggests us to put any custom startup commands in /etc/rc.local,

so I put it there, but it is not executed automatically! Why?

---

### Post by northfly on 2011-05-30
/etc/rc.local is supposed to be executed by /init.d/rc.local if it exist, right?

but why when I put some command here, it is not executed.

please dont suspect my command, the command is good, because I have tried it in ~/.profile, and it works. now I just want this application auto start for all user!!

---

### Post by northfly on 2011-05-30
ok, let me simplify the question: I put sth in the file,

How to make sure the /etc/rc.local is executed when booting?

---

### Post by JKyleOKC on 2011-05-30
When rc.local is executed, there's no PATH variable set, and it executes as the root user. Thus you need to provide the full pathname of the program to rc.local. This is the most common reason for failure to execute commands from there.

To verify that at least some commands are being executed, you can put this line in: ```
echo "rc.local executed at $( /bin/date )" > /rclocal.txt
```and then after booting, do "cat /rclocal.txt" to see that the echo command did execute and create the file. The date and time will tell you precisely when it did so.

---

### Post by tgalati4 on 2011-05-30
Understand that there are several bootup frameworks and they differ from one version of linux to another.  So although /etc/rc.local is a good location for misc. bootup scripts, there are several places to put them and some are better than others.

---

