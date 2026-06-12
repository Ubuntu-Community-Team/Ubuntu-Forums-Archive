---
title: "Problems with vsftpd"
date: 2009-07-11
forum: General Help
---

### Post by jordn on 2009-07-11
Hey all.

vsftpd is causing me serious headaches. i've managed to configure 3 servers using this configuration before but this one has me stumped. 

I am using the standard vsftpd config, with the following adjustments:

```
anonymous_enable=NO
local_enable=YES
write_enable=YES

ssl_enable=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
rsa_cert_file=/root/vsftpd.pem

```

When i restart the vsftpd server, i get this error:

root@xxxx:/var/run# /etc/init.d/vsftpd restart
 * Stopping FTP server: vsftpd                                                           No /usr/sbin/vsftpd found running; none killed.
[ OK ]
 * Starting FTP server: vsftpd                                                           [ OK ]


I use filezilla as my FTP client, and when i try to connect, i get:

```
Error:	Network error: Connection refused
Error:	Could not connect to server
```

The reason i cant connect to my server is because vsftpd doesnt seem to be running at the location /usr/sbin/ but i do not know why. can anyone shed any light on this?

---

### Post by PuK84 on 2009-07-27
You've probably worked this out already, but i was doing a search and no one had replied. I had this problem as well BUT!!! the issue is on the line ssl_tlsvl=YES.

It is supposed to be ssl_tlsv1=YES. the last character befoer the ='s is a one, not an l.

---

