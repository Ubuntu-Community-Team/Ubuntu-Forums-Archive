---
title: "pureftpd    530 access denied"
date: 2011-03-09
forum: General Help
---

### Post by spindler on 2011-03-09
I am successful installed PureFTPD and created a virtual user.   I am testing the access using filezilla from another machine. 

I get the following result

Status:    Connecting to 100.24.180.140:21...
Status:    Connection established, waiting for welcome message...
Response:    220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:    220-You are user number 2 of 50 allowed.
Response:    220-Local time is now 09:02. Server port: 21.
Response:    220-This is a private system - No anonymous login
Response:    220-IPv6 connections are also welcome on this server.
Response:    220 You will be disconnected after 15 minutes of inactivity.
Command:    USER XXX
Response:    331 User XXX OK. Password required
Command:    PASS ********
Response:    530 Login authentication failed
Error:    Critical error
Error:    Could not connect to server

I checked the logging file using PureAdmin  and I found the following:

mar 9. .... ubuntu pure-ftpd : (?@100.24.180.140) [INFO] New connection from 100.24.180.140
mar 9. .... ubuntu pure-ftpd : (?@100.24.180.140) [INFO] PAM_RHOST enabled. Getting the peer address
mar 9. .... ubuntu pure-ftpd : (?@100.24.180.140) [WARNING] Authentication failed for user [XXX]
mar 9. .... ubuntu pure-ftpd : (?@100.24.180.140) [INFO]  logout.


I am not sure if this is a PAM_RHOST configuration problem  or the ftp server does not like the ip address.  I am logging from a different computer on the same network. 

Any ideas as to how to fix this?

---

### Post by spindler on 2011-03-09
So I found a couple of posts that seamed to have solved my problem.

   [http://ubuntuforums.org/showthread.php?t=684590](http://ubuntuforums.org/showthread.php?t=684590)
[http://www.x-fish.org/blog/100128/PureAdmin_vs._PAM_RHOST_enabled/](http://www.x-fish.org/blog/100128/PureAdmin_vs._PAM_RHOST_enabled/)
  

The solution is to run the following:

   
Sudo ln –s /etc/pure-ftpd/conf/PureDV /etc/pure-ftpd/auth/45puredb
  Sudo /etc/init.d/pure-ftpd restart



I am getting a new error

The filezilla output is.

Status:    Resolving address of [www.website.com](www.website.com)
Status:    Connecting to 100.24.180.140:21...
Status:    Connection established, waiting for welcome message...
Response:    220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:    220-You are user number 1 of 50 allowed.
Response:    220-Local time is now 11:16. Server port: 21.
Response:    220-This is a private system - No anonymous login
Response:    220-IPv6 connections are also welcome on this server.
Response:    220 You will be disconnected after 15 minutes of inactivity.
Command:    USER XXX
Response:    331 User XXX OK. Password required
Command:    PASS ********
Response:    230-User XXX has group access to:  xxx   fuse       plugdev   
Response:    230- video      dip        tape       floppy     cdrom      fax       
Response:    230- dialout    adm       
Response:    230 OK. Current directory is /home/xxx
Command:    OPTS UTF8 ON
Response:    200 OK, UTF-8 enabled
Status:    Connected
Status:    Retrieving directory listing...
Command:    PWD
Response:    257 "/home/XXX" is your current location
Command:    TYPE I
Response:    200 TYPE is now 8-bit binary
Command:    PASV
Response:    227 Entering Passive Mode (190,168,1,185,178,159)
Status:    Server sent passive reply with unroutable address. Using server address instead.
Command:    MLSD
Error:    Connection timed out
Error:    Failed to retrieve directory listing


HOW is MLSD handled?

I ready that maybe my firewall is preventing handshaking.   I disabled SPI on my firewall but that did not solve my problem. 

Any ideas?

---

