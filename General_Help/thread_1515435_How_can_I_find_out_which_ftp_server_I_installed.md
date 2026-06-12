---
title: "How can I find out which ftp server I installed?"
date: 2010-06-22
forum: General Help
---

### Post by ashkev on 2010-06-22
I need to make some configuration changes to an ftp server running on Ubuntu server 10.04.  I don't know which ftp server program is installed, so I don't know where to look for the config files.  I know that some server is installed because I can connect to it ;)  

How can I determine which ftp server is installed?

Thanks,

Kevin

---

### Post by cryptotheslow on 2010-06-22
From a terminal prompt:
ps aux |grep ftp

This will find any processes running with ftp in their name.

e.g.
```

graham@gt-desktop:~$ ps aux |grep ftp
proftpd   1185  0.0  0.0   5668  1664 ?        Ss   11:04   0:00 proftpd: (accepting connections)
graham    3823  0.0  0.0   3328   860 pts/0    S+   15:51   0:00 grep --color=auto ftp

```

Most likely it is going to be proftpd or vsftpd

---

### Post by sf-it-services on 2010-06-22
do what he/she said .......:popcorn::lolflag:

---

### Post by gmargo on 2010-06-22
To see what packages are installed, use the **dpkg** command.
```

$ COLUMNS=100 dpkg -l | grep -i ftp | grep -i server
ii  curl                7.18.0-1ubuntu2.2   Get a file from an HTTP, HTTPS or FTP server
ii  ftpd                0.17-27             FTP server
ii  tftpd               0.17-15ubuntu1      Trivial file transfer protocol server

```(Since dpkg reformats its output based on the terminal's column width, I override that with the COLUMNS environment variable.  Usually I use COLUMNS=200 but 100 worked better here.)

An excellent thing to keep on hand is a file with all your installed packages listed.  Then it's easy to **grep** through.  I usually do this:
```

COLUMNS=200 dpkg -l > ~/dpkg-l

```To find out what program is listening on the FTP port, use the **lsof** command:
```

$ sudo lsof -i :ftp
COMMAND   PID USER   FD   TYPE DEVICE SIZE NODE NAME
inetd   11041 root    9u  IPv4  20340       TCP *:ftp (LISTEN)

```

---

