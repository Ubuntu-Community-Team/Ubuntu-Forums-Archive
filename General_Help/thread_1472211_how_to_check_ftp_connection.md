---
title: "how to check ftp connection"
date: 2010-05-04
forum: General Help
---

### Post by Franz01 on 2010-05-04
I have a Ubuntu box with a ftp service on. 
I wanto to upload/download files from my Win XP connected via LAN. 
I tried ftp command from cmd but I received "Error 530. Login incorrect. Login failed".

I'm using root, I am 100% sure about the password (I managed to connect via putty), I just wonder how I can check the ftp connection from xp to ubuntu... maybe a firewall is blocking the port 21?
Or other suggestion?

I also tried ftp command in ubuntu (when I was connected with putty) and I got "connection refused" error.

Thank you

---

### Post by dcstar on 2010-05-05
> **Franz01 said:**
> I have a Ubuntu box with a ftp service on. 
I wanto to upload/download files from my Win XP connected via LAN. 
I tried ftp command from cmd but I received "Error 530. Login incorrect. Login failed".

I'm using root, I am 100% sure about the password (I managed to connect via putty), I just wonder how I can check the ftp connection from xp to ubuntu... maybe a firewall is blocking the port 21?
Or other suggestion?

I also tried ftp command in ubuntu (when I was connected with putty) and I got "connection refused" error.

Thank you

```
telnet ftp-server-whatever 21
```

If the account you are using does not have permissions to use the FTP folder then you can get login errors like that.

---

### Post by Franz01 on 2010-05-05
> **dcstar said:**
> ```
telnet ftp-server-whatever 21
```

If the account you are using does not have permissions to use the FTP folder then you can get login errors like that.

i tried telnet 192.bla.bla.bla 21 and I got the following error: could not open connection to the host, on port 21, connection failed.

But I checked that a proftpd is running in the ubuntu box....

can I say that there must be something in the middle preventing the ftp connection? or do you see other possibilities?

Thank you for any help and suggestion.

---

### Post by dcstar on 2010-05-06
> **Franz01 said:**
> i tried telnet 192.bla.bla.bla 21 and I got the following error: could not open connection to the host, on port 21, connection failed.

But I checked that a proftpd is running in the ubuntu box....

can I say that there must be something in the middle preventing the ftp connection? or do you see other possibilities?

Thank you for any help and suggestion.
If this lists a TCP connection in LISTEN state then the ftp server is running:
```
netstat -na | grep 21
```

---

