---
title: "pure-ftpd connections not working"
date: 2012-08-14
forum: General Help
---

### Post by skinnny on 2012-08-14
Hi

I'm running pure-ftpd 1.0.21 on Ubuntu 9.04, and I'm having trouble connecting over the internet.

This is how I'm starting the server:
```
/usr/local/sbin/pure-ftpd -B -c 10 -C 2 -d -d -E -g $PIDFILE -i -I 10 -l puredb:$PDBFILE -p $MINPASVPORT:$MAXPASVPORT -P $SERVERNAME -S $LISTENPORT -T 500
```
    
I'm using a non-standard, 5-digit LISTENPORT.
MINPASVPORT,MAXPASVPORT is a range of 20 ports just above LISTENPORT.
SERVERNAME is along the lines of ftp.mydomain.com.

My router (Netgear DGN2200) is set to forward port LISTENPORT and port-range MINPASVPORT,MAXPASVPORT to the local-ip of my server.
It's also set to allow all outgoing connections.

Trying to connect to the server from a client over the internet gives the following output in the client:
```
Looking up <SERVERNAME>
Trying <SERVERNAME>:<LISTENPORT>
Connected to <SERVERNAME>:<LISTENPORT>
220---------- Welcome to Pure-FTPd ----------
220-You are user number 1 of 10 allowed.
220-Local time is now 10:09. Server port: <LISTENPORT>.
220-This is a private system - No anonymous login
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 10 minutes of inactivity.
USER <USERNAME>
Error: Could not read from socket: Connection reset by peer
Disconnecting from site <SERVERNAME>
Waiting 30 seconds until trying to connect again
```
    
...and the following output on the server (in /var/log/ftp.log):
```
[INFO] New connection from <CLIENTNAME>
[DEBUG] 220---------- Welcome to Pure-FTPd ----------
[DEBUG] 220-You are user number 1 of 10 allowed.
[DEBUG] 220-Local time is now 10:09. Server port: <LISTENPORT>.
[DEBUG] 220-This is a private system - No anonymous login
[DEBUG] 220-IPv6 connections are also welcome on this server.
[DEBUG] 220 You will be disconnected after 10 minutes of inactivity.
[INFO] Logout.
[DEBUG] 220 Logout.
```

Running "pure-pw list" shows that the <USERNAME> is in the database.

Any ideas?

Colin.

---

