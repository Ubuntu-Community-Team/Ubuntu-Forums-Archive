---
title: "Ubuntu server refusing web connections after update..."
date: 2011-07-22
forum: General Help
---

### Post by Dustin2128 on 2011-07-22
I ran an update on ubuntu server today, and after a long install process, it spat out an error, telling me to run "sudo dpkg --configure -a". After I ran that command, I was no longer able to access my website or forum. I could really use some help with this one, I've tried so many things including disabling shorewall, restarting apache, so many things...

---

### Post by bodhi.zazen on 2011-07-22
> **Dustin2128 said:**
> I ran an update on ubuntu server today, and after a long install process, it spat out an error, telling me to run "sudo dpkg --configure -a". After I ran that command, I was no longer able to access my website or forum. I could really use some help with this one, I've tried so many things including disabling shorewall, restarting apache, so many things...

Hate it when that happens (happened to me recently also).

Can you connect to your server via ssh ? It is possible, but unlikely, some of your configuration files were over written, do you recall what was updated ? Or are you taking upgrade ?

Once you log in, what services are running ? apache ? mysql ? php ?

check to make sure everything is running.

Check the logs for error messages.

Stop your firewall and allow all traffic. Can you connect ?

---

### Post by Dustin2128 on 2011-07-22
> **bodhi.zazen said:**
> Hate it when that happens (happened to me recently also).

Can you connect to your server via ssh ? It is possible, but unlikely, some of your configuration files were over written, do you recall what was updated ? Or are you taking upgrade ?

Once you log in, what services are running ? apache ? mysql ? php ?

check to make sure everything is running.

Check the logs for error messages.

Stop your firewall and allow all traffic. Can you connect ?
I can and am connected via ssh, apache mysql and php are running. As for the updates, I just typed "apt-get update && apt-get dist-upgrade". It was about a month out of date, maverick, and I also upgraded to natty. How do I allow all traffic?

---

### Post by Dustin2128 on 2011-07-23
Babump.

---

### Post by bodhi.zazen on 2011-07-23
> **Dustin2128 said:**
> I can and am connected via ssh, apache mysql and php are running. As for the updates, I just typed "apt-get update && apt-get dist-upgrade". It was about a month out of date, maverick, and I also upgraded to natty. How do I allow all traffic?

I can not tell from what you posted. logs ? apache errors ? mysql errors ?

---

### Post by Dustin2128 on 2011-07-24
Sorry, still somewhat new to the world of servers. Where are the logs stored? Also, would you possibly know how to copy over phpbb data? I'm thinking of migrating this server to something a bit more stable, like debian. I'd still like to fix it though.

---

### Post by bodhi.zazen on 2011-07-25
Logs are in /var/log

I would assume your database is in mysql

---

### Post by Dustin2128 on 2011-07-25
There are many logs in /var/log/apache2, error logs higher than error.log.1 being in .gz format. I assume the latest, error.log.12.gz is the important one here?

---

### Post by Dustin2128 on 2011-07-25
Ah, sorry. The latest ones are the lowest numbers I guess. Anyway, under access.log, I've got this (by browsing to 127.0.0.1 on links):
```

127.0.0.1 -- (22/Jul/2011:18:58:34 =0400] * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)
127.0.0.1 -- (22/Jul/2011:18:58:34 =0400] * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)
127.0.0.1 -- (22/Jul/2011:18:58:34 =0400] * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)
127.0.0.1 -- (22/Jul/2011:18:58:34 =0400] * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)
127.0.0.1 -- (22/Jul/2011:18:58:34 =0400] * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)
```These are the final logs, the rest being earlier access from other computers.

---

### Post by bodhi.zazen on 2011-07-25
Keep looking ;)

[http://wiki.apache.org/httpd/InternalDummyConnection](http://wiki.apache.org/httpd/InternalDummyConnection)

---

