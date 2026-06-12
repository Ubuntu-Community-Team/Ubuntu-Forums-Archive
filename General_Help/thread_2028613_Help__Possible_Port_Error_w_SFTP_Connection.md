---
title: "Help : Possible Port Error w/ SFTP Connection"
date: 2012-07-18
forum: General Help
---

### Post by andrew222 on 2012-07-18
When trying to connect using sftp with key authentication, we are getting this error message.

$  sftp [email]client@hostname.net[/email]#2222
Connecting to [email]client@hostname.net[/email]#2222...
ssh: [email]client@hostname.net[/email]: Hostname and service name not provided or found
Connection closed


Regarding the error message:

	Hostname and service name not provided or found  

This mainly has to do with DNS being not set up properly..


We were able to successfully ping the hostname prior to adding the hostname to /etc/hosts & /etc/resolv.conf,  
so it must not really be a DNS issue.


Given this, we think it may be a port issue.  The host uses 2222 for SFTP.

Can you please advise on what we can do to get SFTP connectivity to this host?

---

### Post by papibe on 2012-07-18
Hi andrew222.

Try this syntax:
```
sftp -p 2222 client@hostname.net
```
Tell us how it goes.
Regards.

---

### Post by andrew222 on 2012-07-18
Thank you papibe...

Trying that syntax didn't work, but your idea led me to use this, which worked...

sftp -oPort=2222 client@hostname

We are using OpenSSH and the host is Tectia.

If we were using Tectia then perhaps your syntax would work.  The people on the host side say #2222 (appended to the end of hostname) will work if the client uses Tectia.

---

