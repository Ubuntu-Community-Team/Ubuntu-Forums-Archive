---
title: "Warning: the RSA host key for '(remote host)' differs from the key for the IP address"
date: 2012-01-12
forum: General Help
---

### Post by zaiger on 2012-01-12
Hello,

I am getting an error when SSHing into my server. I can connect fine via terminal after agreeing to the 'are you sure you want to continue', but when trying to connect via nautilus it is hanging up and timing out because it doesn't show the extra dialogue from the error for me to agree to. I am admittedly not very knowledgeable about key auth, how can I fix something like this?  

Server is Debian 6, I am connecting from my Ubuntu 11.10 AMD64 laptop.

```

Warning: the RSA host key for  '(remote host)' differs from the key for  the IP address '(IP address)'
Offending key for IP in /home/zaiger/.ssh/known_hosts:18
Matching host key in /home/zaiger/.ssh/known_hosts:19
Are you sure you want to continue connecting (yes/no)? 

```

I opened the known_hosts file but had no idea what to do from there. Any help would be great. Thanks in advance

---

### Post by zaiger on 2012-01-12
Ok I fixed it. If anyone happens to find this thread through a search I will explain what I  did.

First I copied the known_hosts and renamed it for a backup.
```
cp ~/.ssh/user/known_hosts ~/.ssh/user/known_host_backup
```
and then deleted the known_hosts file altogether and replaced it with a brand new document with the same name. Apparently my server's IP is dynamic and that is why it was confused.

Thanks anyways!

---

### Post by polki@mac.com on 2012-01-12
Just adding some info.

If you have a lot of entries in your known_host it's easier to just erase the line indicated by the error message:

Matching host key in /home/zaiger/.ssh/known_hosts:**19**

Please note that it's a security message, something could be wrong. Better check things out first.

---

### Post by Habitual on 2012-01-12
> **zaiger said:**
> Ok I fixed it. First I copied the known_hosts and renamed it for a backup.
```
cp ~/.ssh/user/known_hosts ~/.ssh/user/known_host_backup
```

IMO, you didn't 'fix' anything, *you ignored the issue twice*, once on warning and once when you renamed the very file that is doing it's job...Checking remote hosts for anomalous issues that affect Security.

[email]polki@mac.com[/email] is 100% correct, 
Ball is in your court.

---

