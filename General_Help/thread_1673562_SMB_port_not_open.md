---
title: "SMB port not open"
date: 2011-01-22
forum: General Help
---

### Post by Almost A Ghost on 2011-01-22
Did a fresh install of Ubuntu Desktop 10.10 64-bit on my Dell D630.

I installed the Samba and used GADMIN-Samba to configure. The networking area is as follows:

Allowed hosts and networks: 127. 192.168.0.
Handle Connections on: 127.0.0.1/8 192.168.0.0/24
Announce this server to: 192.168.0.255
Retrieve Announcements from: 192.168.0.255

But I'm am unable to attach to the SMB share. When I do a port scan on the PC network address it shows the port for SSH open along with the random high number ports for web connections but not the port for SMB (445). If I port scan 127.0.0.1 it shows SSH, netbios-ssn, and SMB open.

I've tried adding a rule to UFW and disabling UFW but it makes no difference.

I'm able to connect to SMB shares off of my Windows Desktop, so I know my home router isn't filtering any internal traffic.

---

### Post by efflandt on 2011-01-22
On the Dell, what shows for: **netstat -nlt**

---

### Post by Almost A Ghost on 2011-01-22
> **efflandt said:**
> On the Dell, what shows for: **netstat -nlt**

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:139           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:445           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:27169           0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
michael@LVIS07:~$

---

### Post by Almost A Ghost on 2011-01-23
Bump :(

---

### Post by Almost A Ghost on 2011-01-24
I restarted the SMB service and it is now listening on the network IP. The issue is that I have to restart it every time I restart the computer.

---

