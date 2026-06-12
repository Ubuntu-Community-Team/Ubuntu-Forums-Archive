---
title: "ftp: connect :Unknown error number"
date: 2009-08-10
forum: General Help
---

### Post by codingfreak on 2009-08-10
Hi

I am using **VSFTPD** on my FC9 machine. It is working fine for all these days but suddenly it started showing

```
> ftp: connect :Unknown error number
```when I try to FTP to  the machine. I can still telnet to the Linux Server but not able to do FTP.

---

### Post by DaithiF on 2009-08-11
Hi,
On your fedora box, is the vsftpd service running?  (i'm not a fedora user, but something like ```
/sbin/service vsftpd status
```, i think)
On your client machine, do you have a firewall enabled?  could it be blocking port 21 (or whichever port you have configured vsftpd to listen on?)
Can you ftp in from any other client machines?

---

### Post by codingfreak on 2009-08-12
I see that FTP service is running in my FEDORA box .....

I am not able to connect through any of the client PCs through FTP ......

---

