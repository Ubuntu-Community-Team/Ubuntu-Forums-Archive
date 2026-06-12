---
title: "gFTP/ftp Error"
date: 2006-04-20
forum: General Help
---

### Post by coringibson on 2006-04-20
Hey everyone...I'm having a little problem with ftp on my machine.

About 85% of the time ftp (i've tried many clients like gftp, cli ftp, igloo, etc...) gives me an error that says "Could not read from socket: Connection reset by peer". I tried passive mode, and it gave me a 'no route to host' error.

I tried using FileZilla through wine, and it works like a charm...i've tried different ftp sites, and some work but others dont. I'm fairly sure this is a problem with the Ubuntu confirguration itself...I sit right next to someone who has no problems at all (and is running windows).

Any ideas? It was suggested that I may be having internet problems (like a bad physical connection), but I am able to access any other thing on 'teh intarweb'.

Here is my gFTP output when I try to get on this server...any help would be appreciated.

Looking up ftp.***.com
Trying ftp.***.com:21
Connected to ftp.***.com:21
220---------- Welcome to Pure-FTPd [TLS] ----------
220-You are user number 7 of 50 allowed.
220-Local time is now 15:17. Server port: 21.
220-This is a private system - No anonymous login
220 You will be disconnected after 15 minutes of inactivity.
USER ***

331 User *** OK. Password required
PASS xxxx
230-User *** has group access to:  ***     
230 OK. Current restricted directory is /
SYST

215 UNIX Type: L8
TYPE I

200 TYPE is now 8-bit binary
CWD /www

250 OK. Current directory is /www
Loading directory listing /www from server (LC_TIME=en_US.UTF-8)
PORT 10,20,1,130,128,34

Error: Could not read from socket: Connection reset by peer
Disconnecting from site ftp.***.com

---

