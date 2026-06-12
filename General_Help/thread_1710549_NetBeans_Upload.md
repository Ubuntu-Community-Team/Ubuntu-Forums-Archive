---
title: "NetBeans Upload"
date: 2011-03-20
forum: General Help
---

### Post by snake_eyes on 2011-03-20
Hi,

It was working well unless I updated the Ubuntu 10.10, I have the NetBeans installed on my 10.4 and the 10.10 is the server, I opened the source code via the NetBeans and I set On Save event through NetBeans Upload the changes, Early I'm getting "Upload On Save Failed" with the following IDE Error:

```
INFO [org.netbeans.modules.php.project.copysupport.RemoteOperationFactory]: Upload failed: org.netbeans.modules.php.project.connections.TransferInfo [transfered: [], failed: {degrees.php=425 Could not open data connection to port 57949: Connection refused}, partially failed: {}, ignored: {}, runtime: 236 ms]
INFO [org.netbeans.modules.php.project.copysupport.RemoteOperationFactory]: Upload failed: org.netbeans.modules.php.project.connections.TransferInfo [transfered: [], failed: {degrees.php=425 Could not open data connection to port 40928: Connection refused}, partially failed: {}, ignored: {}, runtime: 14 ms]
```

Any Idea about the problem? Although all ports are opened and I tried net cat all ports success plus the FTP Server is running.

Sincerely,

---

### Post by snake_eyes on 2011-03-20
I noticed that the problem is from my FTP server, I tried to login in order to test the FTP and prove that the problem is not from the netbeans, kindly see the result below:

```
ftp> open ftpserver
Connected to ftpserver.
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 2 of 50 allowed.
220-Local time is now 10:19. Server port: 21.
220-This is a private system - No anonymous login
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
Name (ftpserver:sysmin): james
331 User james OK. Password required
Password:
230-User james has group access to:  james    fuse       plugdev   
230- video      dip        tape       floppy     cdrom      fax       
230- dialout    adm       
230 OK. Current directory is /home/james
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> pwd
257 "/home/james" is your current location
ftp> cd ww
550 Can't change directory to ww: No such file or directory
ftp> cd www
250 OK. Current directory is /home/james/www
ftp> ls
200 PORT command successful
425 Could not open data connection to port 47707: Connection refused
ftp> ls
200 PORT command successful
425 Could not open data connection to port 46782: Connection refused
ftp>
```
Any help?

---

