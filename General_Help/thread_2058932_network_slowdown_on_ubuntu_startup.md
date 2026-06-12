---
title: "network slowdown on ubuntu startup"
date: 2012-09-16
forum: General Help
---

### Post by superbike on 2012-09-16
Recently I have been having a problem with my ubuntu server installation.
It is a torrent(transmission-daemon) and ftp(proftpd) server running on  an old atom box with 2G ram. It also has a LAMP server running.
As soon as i start my server the whole network suffers a slowdown. i  tested even by stopping both the transmission and proftp daemons but the  problem persists **please help**.
:cry:
I have tried updating and all possible things. Even the connection on the box is hopelessly slow.

Thanx in anticipation

---

### Post by beboylips on 2012-09-17
Run $netstat -tupn on your server box. Also check your router statistics (if possible).

---

### Post by superbike on 2012-09-17
issued the command netstat



gaurav@abenawe:~$ sudo netstat -tupn
  [sudo] password for gaurav:
  Active Internet connections (w/o servers)
  Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
  tcp        0      0 127.0.0.1:80            127.0.0.1:34320         TIME_WAIT   -
  tcp        0      1 192.168.1.9:35191       10.20.30.1:2048         SYN_SENT    1430/transmission-d
  tcp        0      0 127.0.0.1:60290         127.0.0.1:4712          ESTABLISHED 1323/amuleweb
  tcp        0      0 127.0.0.1:4712          127.0.0.1:60290         ESTABLISHED 1299/amuled
  tcp        0      0 192.168.1.9:22          192.168.1.2:56635       ESTABLISHED 1782/sshd: gaurav [
  udp        0      0 192.168.1.9:49473       192.168.1.1:5351        ESTABLISHED 1430/transmission-d

---

