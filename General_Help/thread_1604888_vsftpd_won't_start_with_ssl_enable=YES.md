---
title: "vsftpd won't start with ssl_enable=YES"
date: 2010-10-24
forum: General Help
---

### Post by Glandoux on 2010-10-24
Bump
 
Hello everyone!
 
I'm in need for some help here with vsftpd.
 
My problem right now is i'm trying to configure vsftpd to work with ssl.
 
My vsftpd is configured with virtual users and everything works fine (without ssl).
I can ftp to the server from a client on the same network.
 
Now when i try to enable ssl, the server won't start at all.
Actually, if i run service vsftpd start, it look like it is starting, but if i check the processes, vsftpd is not there, and obviously, if i try to ftp, it fails.
 
So as soon as i turn ssl_enable=YES in vsftpd.conf, vsftpd won't start
 
The only message i get is in /var/log/daemon.log
init: vsftpd main process (6407) terminated with status 1
init: vsftpd respawning too fast, stopped
 
Any idea what the problem could be?
I've been searching a lot for this problem, but i didn't find anything good yet.
 
thanks,

---

### Post by Glandoux on 2010-10-27
Bump, haven't find a solution yet..
Somebody can help me?
thanks,

---

### Post by duckworth397 on 2010-11-25
I was having the same issue when I was trying to set up ssl using a real cert. Adding the path to the private key as well as the public key finally got it working.

```
rsa_cert_file=/etc/vsftpd/vsftpd.pem
rsa_private_key_file=/etc/vsftpd/vsftpd.key
```

---

### Post by tkess on 2011-06-15
Thanks....just saved me some time.  Same issue.  Fix worked.

---

