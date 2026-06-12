---
title: "netstat help (remote vs local accessible services)"
date: 2010-01-06
forum: General Help
---

### Post by manolo_asdf on 2010-01-06
hi, i am trying to keep as many service non-remote as possible. for that i executed:

```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN      30416/sendmail: MTA
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      30324/cyrmaster 
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      30324/cyrmaster 
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      18162/apache2   
tcp        0      0 127.0.0.1:2000          0.0.0.0:*               LISTEN      30324/cyrmaster 
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      22327/sshd      
tcp        0      0 0.0.0.0:119             0.0.0.0:*               LISTEN      30324/cyrmaster 
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      30416/sendmail: MTA
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      18162/apache2   
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      30230/mysqld    
tcp6       0      0 :::110                  :::*                    LISTEN      30324/cyrmaster 
tcp6       0      0 :::143                  :::*                    LISTEN      30324/cyrmaster 
tcp6       0      0 :::22                   :::*                    LISTEN      22327/sshd      
tcp6       0      0 :::119                  :::*                    LISTEN      30324/cyrmaster 
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     2368264  30230/mysqld        /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     2368815  30324/cyrmaster     /var/run/cyrus/socket/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     2368896  30416/sendmail: MTA /var/run/sendmail/mta/smcontrol


```

what is a bit unclear to me: how do i see whether a service is remotely accessible or not. i guess 127.0.0.1 says it is only available on same machine. 0.0.0.0 says that it listens to all network interfaces, i.e. is visible from outside

i ran telnet on the 127.0.0.1+ port entries and i got connection refused, so i guess i am right?

thanks.

---

### Post by tquinn on 2010-01-15
Did you find an answer to this?

I am having an associated problem getting my Java program to be accessible from other machines via TCP.

---

