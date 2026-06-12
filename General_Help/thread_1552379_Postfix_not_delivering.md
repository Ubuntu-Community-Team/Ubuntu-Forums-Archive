---
title: "Postfix not delivering"
date: 2010-08-13
forum: General Help
---

### Post by Moptop650 on 2010-08-13
Hi all, I'm trying to set up postfix as a mail server on my Ubuntu Server.

I followed this tutorial EXACTLY: [http://howtoforge.com/perfect-server-ubuntu8.04-lts-p5](http://howtoforge.com/perfect-server-ubuntu8.04-lts-p5) , including the last part where Maildir is chosen. 

Clarification - I can send mail from my server, but can't receive mail sent to it. Connecting with Pop3 works fine, but always says there's no messages.

Nothing relevant gets printed to any of the /var/log/mail.* files.

After following that tutorial I:

> 
Created /etc/postfix/local-host-names and filled it with
```
localhost
davepedu.com
vps.xmop.org


```

Created /etc/postfix/virtusertable and filled it with
```
dave@davepedu.com dave


```

Ran:
```
postconf -e 'virtual_maps = hash:/etc/postfix/virtusertable'
postconf -e 'mydestination = /etc/postfix/local-host-names'
postmap /etc/postfix/virtusertable
/etc/init.d/postfix restart
```


I've tried the whole set up a few times today, one of which worked and mysteriously stopped working a few hours later. I don't think I did much different between them.

My /etc/postfix/main.cf can be seen here: [http://184.82.43.12/main.cf](http://184.82.43.12/main.cf)

I just don't know what else I can do :(. The mail seems to be going nowhere, nothing appears anywhere in /home/dave/Maildir, and /var/mail/dave remains untouched.

Any help is appreciated :)

---

