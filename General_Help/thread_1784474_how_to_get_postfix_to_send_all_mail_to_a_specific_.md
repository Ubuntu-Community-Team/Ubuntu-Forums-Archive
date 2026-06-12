---
title: "how to get postfix to send all mail to a specific address"
date: 2011-06-17
forum: General Help
---

### Post by tigerstripedcat on 2011-06-17
This *HAS* to be a common problem

Problem: you run a ubuntu machine but you dont run an smtp server so your logs and error messages are being mailed around to different built in users (root, www-data, etc.) on your machine but you have no access to this info unless you check your local mail on a regular basis

Solution: set up postfix to gmail SMTP servers to forward all mail to your email address  I used these two guides to acomplish this:

[http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/](http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/)
[http://www.debian-administration.org/articles/604](http://www.debian-administration.org/articles/604)

The first is probably all you really need.

New problem:  Your computer is not part of any real domain out on the internet so when users (like root or www-data or cron, etc.) want to send mail it gets set to "root@" or "root@localhost" so the solution above does its fancy rerouting and now you are trying to send mail to [email]root@gmail.com[/email] or other addresses.  

Question: Can someone tell me if there is a setting in postfix/main.cf where *ALL* mail can be sent to a external address somewhere?  I can't seem to get this to work for the life of me. (And the problem is there should really really really be a HOWTO on this because you would think this is something EVERYONE would want to do on their systems.)

---

