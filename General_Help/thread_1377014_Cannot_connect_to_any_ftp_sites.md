---
title: "Cannot connect to any ftp sites"
date: 2010-01-09
forum: General Help
---

### Post by bluewagon on 2010-01-09
Ever since restarting from an Ubuntu update (I don't remember what all of it was updating) I have been unable to connect to FTP sites. My connections all timeout, ive tried using firefox, nautilus, and filezilla but they all timeout.
Does anyone know of any way to fix this problem?

---

### Post by dcstar on 2010-01-10
> **bluewagon said:**
> Ever since restarting from an Ubuntu update (I don't remember what all of it was updating) I have been unable to connect to FTP sites. My connections all timeout, ive tried using firefox, nautilus, and filezilla but they all timeout.
Does anyone know of any way to fix this problem?

First you test your network by:

```
telent ftpsite.wherever.com 21
```

And if you get a response from the remote server then the networking is ok, if not then something is blocking access - anywhere from your system to your ISP to the remote server.

---

### Post by sanderj on 2010-01-10
What happens if you a terminal, and then type 

```
ftp ftp.xs4all.nl
```

See below.


```
sander@quirinius:~$ ftp ftp.xs4all.nl
Connected to ftp2.xs4all.nl.
220 XS4ALL ftpd DCLXVI
Name (ftp.xs4all.nl:sander): ftp
331 Anonymous login ok, send your complete email address as your password.
Password:
230-
 Welkom op de FTP server van XS4ALL
 ----------------------------------
 
230 Anonymous access granted, restrictions apply.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> bye
221 Goodbye.
sander@quirinius:~$

```

---

### Post by rnerwein on 2010-01-10
hi 
i think you should start at the base - this means first have a lookup at your interfaces:
ifconfig -a   -> is/are the interface(s) UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1 ....
if they are up (inetaddr. etc is ok) try
ping or ssh to connect to anybody (telnet and ftp are mostly blocked by firewall rules :-!
cia

---

