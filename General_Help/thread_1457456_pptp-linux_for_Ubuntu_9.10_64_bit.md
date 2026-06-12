---
title: "pptp-linux for Ubuntu 9.10 64 bit"
date: 2010-04-18
forum: General Help
---

### Post by Alex Farber on 2010-04-18
I am trying to connect to the Internet using installation package from my Internet provider. After successful installation, I run connection script:

```

alex@alex-64:~$ sudo cable-start
[sudo] password for alex: 
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sh: /usr/sbin/pptp-linux: not found
Modem hangup
Connection terminated.

```

Provider installation package contains pptp-linux program. In Ubuntu 32 bit I just copied it to sbin directory, and connection succeeded. In 64 bit, after copying this file, I have:

```

alex@alex-64:~$ file /usr/sbin/pptp-linux
/usr/sbin/pptp-linux: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped
alex@alex-64:~$ /usr/sbin/pptp-linux
bash: /usr/sbin/pptp-linux: No such file or directory

```

It looks like pptp-linux that I have cannot be executed in 64 bit OS. Is it possible to run this program by some way, or install it? I don't have Internet connection on 64 bit system, but I am connected from 32 bit system, and can download required files.

---

### Post by Alex Farber on 2010-04-19
Solved by installing pptp-linux from installation CD.

---

