---
title: "FTP on Ubuntu"
date: 2009-09-01
forum: General Help
---

### Post by Strega on 2009-09-01
Hello,

Before I ask my question I will give you a few links wich will let you know what kind of machine I got and where I got it from.

The server I bought :
[http://www.hetzner.de/de/hosting/produkte_rootserver/eq4/](http://www.hetzner.de/de/hosting/produkte_rootserver/eq4/)
It's specs :
[http://188.40.79.137/phpsysinfo/](http://188.40.79.137/phpsysinfo/)

So, my question...
I've tried to install proftpd on my machine and log in, but that didn't work.
I already posted this, but in a wrong section.
Here is the link (the 4 last posts) :
[http://ubuntuforums.org/showthread.php?t=1251330&page=2](http://ubuntuforums.org/showthread.php?t=1251330&page=2)
He told me something about changing a config, but I have no idea what to put in it.
You have any ideas?

Regards, Strega

---

### Post by jonobr on 2009-09-01
Hello


Is the ftp server on the same machine?
i.e. 188.40.79.137


If so, it appears the daemon is listening and its a user authentication issue,
is this what you are seeing when you ftp?
```

me@here:~$ ftp 188.40.79.137
Connected to 188.40.79.137.
220 ProFTPD 1.3.1 Server 
Name (188.40.79.137:here): 

```

---

### Post by Strega on 2009-09-01
> **jonobr said:**
> Is the ftp server on the same machine?
i.e. 188.40.79.137
Yes, I only have 1 IP for my server, so the ftp server should be on the same one :p

> **jonobr said:**
> is this what you are seeing when you ftp?
```

me@here:~$ ftp 188.40.79.137
Connected to 188.40.79.137.
220 ProFTPD 1.3.1 Server 
Name (188.40.79.137:here): 

```
No, the thing I see is this
```

Resolving 188.40.79.137...  
188.40.79.137 connecting...  
220 ProFTPD 1.3.1 Server (Debian) [::ffff:188.40.79.137]  
SFTP connection error - The current connection has timeout
Can't establish connection --> 188.40.79.137:21 @ Tue Sep 01 22:09:52 2009   (0-1460)

```

Should I uninstall the proftpd and reinstall it?
I also have another ftp installed, but that one is turned of.
I would like to uninstall that to, but I don't know how to uninstall something, I'm just a beginner in Ubuntu you know :p

Thanks for the replie, Strega

---

### Post by jonobr on 2009-09-01
Hello


The ftp I posted shows FTPis working and responding to my request to autheticate to your machine,

You are using SFTP, secure ftp 

So, it sounds as if your not using SSH which is what SFTP uses.
Do you have this installed?


I would recommend If you want a secure connection between client and server,
install openssh from synaptic, and use scp instead
then from a windows machine, you can use a program called winscp which has a simple explorer style interface for copying,

or you could use the places->connect to serveroption if connecting from a ubuntu box.
Or you could ditch all that and run command line.

---

### Post by jonobr on 2009-09-01
investigating this further, you need an SFTP module for proftpd you can see it [HERE]("http://www.proftpd.org/module_news.html")

> SFTP module
Maintainer: TJ Saunders
[http://www.castaglia.org/proftpd/modules/mod_sftp.html](http://www.castaglia.org/proftpd/modules/mod_sftp.html)

The mod_sftp module implements the SSH2, SFTP and SCP protocols, allowing SCP and SFTP clients to be used with ProFTPD. ProFTPD's existing features such as flexible logging, chrooted logins, SQL/LDAP/RADIUS support, quotas, etc can be used for SCP and SFTP clients.


I would stick with the openssh and scp approach, but thats just me

---

