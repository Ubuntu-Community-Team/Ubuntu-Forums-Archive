---
title: "Cannot add users to mail server stack"
date: 2011-08-23
forum: General Help
---

### Post by stepheny on 2011-08-23
I have installed the mail-server-stack in 11.04 but after installation postfix couldn't write to a new users /Maildir directory. This was obviously a permissions problem but I couldn't add the postfix user to the users group using Unity System Settings - Users and Groups because it didn't appear there. I added the postfix user from the console like this and it solved this problem

```
sudo adduser postfix barbara 
```

But now whenever I try and read rhe contents of the new users /Maildir via thunderbird using the new users password I get an authorization failure.

I have tried using my Dovecot, Postfix, Procmail and Fetchmail configuration files which still work under 10.04 in the 11.04 installation and they don't work either, giving the same authorization error.

Syslog tells me 

```
dovecot pop3-login:Disconnected (auth failed, 2 attempts): user=<barbara>, method=plain, rip=192.168.0.x, lip=192.168.0.y
```

---

