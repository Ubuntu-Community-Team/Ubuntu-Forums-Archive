---
title: "Help! Stop Syslog!!"
date: 2010-03-13
forum: General Help
---

### Post by Bondy_uk on 2010-03-13
Hi everyone,

For the last couple of days ive noticed my PC (Ubuntu 9.04 x64) has been accessing the HDD a lot.

Basically when idle, about every minute by HDD makes noises.
Or more often, whenever I do anything: even change webpage, change a Window from one app to another, etc.

If I was in Windows I would have thought it was a keylogger type virus.

So I installed iotop (HDD monitor) and it shows that every minute or so, when I can hear the noise, Syslog is writing to HDD.

It shows Syslog as 'user' - but also sometimes shows 'root' and/or 'ian' writing to disk at the same time too.

I dont understand why this has just started, and from what I can gather this is basically a webserver log? 
Ive never set it up like this, it is purely a desktop PC, and it only started a couple of days ago!!


I dont know what to do, or why this is happening :shock:

Can someone help with shutting this down permanently or even provide an insight into why this is running in the first place ?


Thanks,
Ian

---

### Post by Slim Moe on 2010-03-13
Before you try to stop it, read what [syslog-ng]("http://en.wikipedia.org/wiki/Syslog-ng") is.

---

### Post by Bondy_uk on 2010-03-13
Hi,

Thanks for your reply.

Ok so I read that and im still confused WHY I would need this on my PC or WHY this started 2 days ago by itself?? 

So wikipedia says:
> syslog-ng is an open source implementation of the Syslog protocol for Unix and Unix-like systems.

Ok so I clicked on syslog (the original) and wiki says:
> Syslog is a standard for forwarding log messages in an Internet Protocol (IP) computer network. It allows separation of the software that generates log messages from the system that stores the messages.

Syslog is a client/server protocol:[1] a logging application transmits a maximum 1024-byte text message to the syslog receiver. The receiver is commonly called syslogd, syslog daemon or syslog server


This still makes no sense to me why this suddenly started, why you would need it on a home desktop PC, or why this is writing to disk once every minute continuously for the last couple of days??


Is this some form of keylogging or a Linux hack for remote exploitation or something?
It just seems like its constantly monitoring & recording the PC and I dont understand why. Apart from that my main concern is that its going to kill my HDD with all the constant accessing!

So is Syslog safe to remove/disable and if so, how do I do it?

---

### Post by dcstar on 2010-03-13
> **Bondy_uk said:**
> 
.........
This still makes no sense to me why this suddenly started, why you would need it on a home desktop PC, or **why this is writing to disk once every minute continuously for the last couple of days?**?


Is this some form of keylogging or a Linux hack for remote exploitation or something?
It just seems like its constantly monitoring & recording the PC and I dont understand why. Apart from that my main concern is that its going to kill my HDD with all the constant accessing!

So is Syslog safe to remove/disable and if so, how do I do it?

Perhaps **if you actually looked** at the Syslog file you would see what is happening with your system?

Or you can wait until the whole thing crashes because log messages have been ignored......

---

### Post by Bondy_uk on 2010-03-13
Ok well thanks for your condescending help there.
It was obvious I didnt have a clue what was going on/what this is.

At the end of the day as I said before, from what I was reading nothing said it was any kind of desktop PC log. It was to do with/is a Webserver log. Why would a webserver log be running on my PC...

Well I guess when I have time in a couple of days I will have to try and find out how you read this apparent webserver log running on my PC.
Or if I cant, wait until it buggers the PC up. Of course it would have been handy if it was made obvious im supposed to be looking for some file or there was even a problem its trying to 'log', like some kind of message/notification system.

---

### Post by rnerwein on 2010-03-14
hi
it would be nice to see what's in your lock and what logfile you are talking about. sylog is managing a
couple of locks.
if you talk about a unknown webserver - are you talking about:
rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1048" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
this is a normal message (if you ain't have thausends of them ) you can ignore it ( i know what happen ).
ciao

---

### Post by mcduck on 2010-03-14
> **Bondy_uk said:**
> Ok well thanks for your condescending help there.
It was obvious I didnt have a clue what was going on/what this is.

At the end of the day as I said before, from what I was reading nothing said it was any kind of desktop PC log. It was to do with/is a Webserver log. Why would a webserver log be running on my PC...

Well I guess when I have time in a couple of days I will have to try and find out how you read this apparent webserver log running on my PC.
Or if I cant, wait until it buggers the PC up. Of course it would have been handy if it was made obvious im supposed to be looking for some file or there was even a problem its trying to 'log', like some kind of message/notification system.

I'm not sure what made you think syslog would be intended, or in some way even related, to web servers.

Sure, it does use IP (as do many other things in Linux, using IP doesn't *always* mean that the data wold actually travel through network, it is commonly used to handle connections* inside* your system). And it *can* send data through networks. Biut it doesn't unless you configure it to do something like that.

Simply put, syslog is the way all your programs and system services can write to the same log files on your system. Instead of each program/service writing to their own log files or trying to access the same log files all the others are trying to write to, they send the log messages to syslog which then writes them to log files.

So it sure s something that is supposed to be running on every Linux system, has nothing to do with web servers, and sure has been running from the very day you installed Ubuntu.

(The Apache web server pretty much keeps it's own logs since no other program needs to write to them, and those would be in /var/log/apache2/ if you had Apache installed.)

(also the part in Wikipedia about syslog using a client/server protocol has nothing to do with web servers and such. That simply means that the part that creates the log messages and the part that writes then to actual log files are separated,a s I described above. Syslog is the "server" that writes the log files, while the clients are all the programs that send log messages.)

---

### Post by asmoore82 on 2010-03-14
It's probably not a good idea to turn off Syslog.

Watching this for a few minutes should give you an idea as to which logfile has
been written to most recently, and hence which one you should read the end of:
```
watch -d ls -lot /var/log
```
^use Control+C to stop it

If you are not behind a Firewall and have SSH running,
My first guess would be that someone is trying to brute force your password.
Happens to me all of the time ~ "I hear you knocking but you can't come in..."

---

### Post by Slim Moe on 2010-03-14
> **Bondy_uk said:**
> 
At the end of the day as I said before, from what I was reading nothing said it was any kind of desktop PC log. It was to do with/is a Webserver log. Why would a webserver log be running on my PC...

It's a system log file, not related to web servers or whatever you might have understood. Read the log file ( or simply post it here so that one could help you ) and see what's being written to it.

---

### Post by Bondy_uk on 2010-03-14
Thank you everyone for taking the time to help. Everything seems a bit clearer now!

> **mcduck said:**
> 
(The Apache web server pretty much keeps it's own logs since no other program needs to write to them, and those would be in /var/log/apache2/ if you had Apache installed.)


I realise its probably unrelated, but when I looked in Services Apache is apparently installed and running - although I have never installed or used it before :confused:
Is Apache only used to act as a webserver (such as hosting a website on your PC and using a dynamic DNS service to point a domain to it) or could it be required to run another program / auto installed with something else?


> **asmoore82 said:**
> It's probably not a good idea to turn off Syslog.

Watching this for a few minutes should give you an idea as to which logfile has
been written to most recently, and hence which one you should read the end of:
```
watch -d ls -lot /var/log
```
^use Control+C to stop it

If you are not behind a Firewall and have SSH running,
My first guess would be that someone is trying to brute force your password.
Happens to me all of the time ~ "I hear you knocking but you can't come in..."


Right this has just raised more questions! lol
Apparently its a mail thing (im assuming email?) - but the first thing I always do when I install is remove unwanted programs (Evolution being one of them). I have never used it and hasnt given me trouble before.

The files being highlighted are:
```
total 234596
-rw-r----- 1 syslog  13846604 2010-03-14 21:52 mail.info
-rw-r----- 1 syslog  13846604 2010-03-14 21:52 mail.log
-rw-r----- 1 syslog  13861803 2010-03-14 21:52 syslog
-rw-r----- 1 syslog   7924691 2010-03-14 21:52 mail.err
-rw-r----- 1 syslog   7924691 2010-03-14 21:52 mail.warn
-rw-r----- 1 syslog    992729 2010-03-14 21:50 auth.log
-rw-r----- 1 syslog    619492 2010-03-14 21:45 messages
-rw-rw-r-- 1 root       74112 2010-03-14 21:31 wtmp
```

Its a bit random, sometimes wtmp, messages and auth.log are being highlighted independantly and other times they arent.

---

### Post by Bondy_uk on 2010-03-14
**_syslog_**

```
Mar 14 22:33:57 ian-Ubuntu64 nullmailer[2590]: smtp: Failed: Connect failed
Mar 14 22:33:57 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:57 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268418001.22337
Mar 14 22:33:57 ian-Ubuntu64 nullmailer[2591]: smtp: Failed: Connect failed
Mar 14 22:33:57 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:57 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268523601.13679
Mar 14 22:33:57 ian-Ubuntu64 nullmailer[2592]: smtp: Failed: Connect failed
Mar 14 22:33:57 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:57 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268409602.26357
Mar 14 22:33:57 ian-Ubuntu64 nullmailer[2593]: smtp: Failed: Connect failed
Mar 14 22:33:57 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268478001.18815
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2597]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268601002.8967
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2598]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268430601.20031
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2602]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268416801.13584
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2603]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268459402.27056
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2604]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268369401.26157
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2608]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268403601.16370
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2609]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268601602.15531
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2610]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268404802.24773
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2611]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268425202.11367
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2612]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268036882.9625
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2613]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268560202.2794
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2614]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268450401.16410
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2615]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268602201.22153
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2616]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268570401.9017
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[2617]: smtp: Failed: Connect failed
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:33:58 ian-Ubuntu64 nullmailer[3129]: Delivery complete, 278 message(s) remain.
```


_**mail.log**_
```
host: mail. file: 1268560202.2794
Mar 14 22:27:53 ian-Ubuntu64 nullmailer[30770]: smtp: Failed: Connect failed
Mar 14 22:27:53 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:27:53 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268450401.16410
Mar 14 22:27:53 ian-Ubuntu64 nullmailer[30771]: smtp: Failed: Connect failed
Mar 14 22:27:53 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:27:53 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268602201.22153
Mar 14 22:27:53 ian-Ubuntu64 nullmailer[30772]: smtp: Failed: Connect failed
Mar 14 22:27:53 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:27:53 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268570401.9017
Mar 14 22:27:53 ian-Ubuntu64 nullmailer[30776]: smtp: Failed: Connect failed
Mar 14 22:27:53 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:27:53 ian-Ubuntu64 nullmailer[3129]: Delivery complete, 277 message(s) remain.
```


_**mail.info**_
```
host: mail. file: 1268450401.16410
Mar 14 22:29:07 ian-Ubuntu64 nullmailer[31607]: smtp: Failed: Connect failed
Mar 14 22:29:07 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:29:07 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268602201.22153
Mar 14 22:29:07 ian-Ubuntu64 nullmailer[31608]: smtp: Failed: Connect failed
Mar 14 22:29:07 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:29:07 ian-Ubuntu64 nullmailer[3129]: Starting delivery: protocol: smtp host: mail. file: 1268570401.9017
Mar 14 22:29:07 ian-Ubuntu64 nullmailer[31609]: smtp: Failed: Connect failed
Mar 14 22:29:07 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:29:07 ian-Ubuntu64 nullmailer[3129]: Delivery complete, 277 message(s) remain.
```


**_mail.err_**
```
Mar 14 22:31:27 ian-Ubuntu64 nullmailer[861]: smtp: Failed: Connect failed
Mar 14 22:31:27 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:27 ian-Ubuntu64 nullmailer[862]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[863]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[864]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[865]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[866]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[870]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[871]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[872]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[873]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[874]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[875]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[876]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[877]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[878]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[880]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[883]: smtp: Failed: Connect failed
Mar 14 22:31:28 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
```


_**mail.warn**_
```
Mar 14 22:32:43 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:43 ian-Ubuntu64 nullmailer[1743]: smtp: Failed: Connect failed
Mar 14 22:32:43 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:43 ian-Ubuntu64 nullmailer[1744]: smtp: Failed: Connect failed
Mar 14 22:32:43 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:43 ian-Ubuntu64 nullmailer[1745]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[1746]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[1747]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[1748]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[1749]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[1750]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[1754]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[1755]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[1756]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[1757]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[1758]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[1759]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[1760]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[1761]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[1762]: smtp: Failed: Connect failed
Mar 14 22:32:44 ian-Ubuntu64 nullmailer[3129]: Sending failed:  Host not found
```

---

### Post by Bondy_uk on 2010-03-14
All I did what a quick selection of the last bits of the files/logs. I tried to copy and paste the entire log twice and it crashed my pc both times :frown:

So is this saying its trying to send emails or something?


Does it help to see some of my auth.log? (since its another one that keeps flashing?)

```
Mar 14 22:24:00 ian-Ubuntu64 dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.41" (uid=1000 pid=4691 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.77" (uid=1000 pid=28114 comm="/usr/lib/firefox-3.0.18/firefox "))
Mar 14 22:26:35 ian-Ubuntu64 dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.41" (uid=1000 pid=4691 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.78" (uid=1000 pid=29789 comm="/usr/lib/firefox-3.0.18/firefox "))
Mar 14 22:30:01 ian-Ubuntu64 CRON[32021]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 14 22:30:01 ian-Ubuntu64 CRON[32020]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 14 22:30:01 ian-Ubuntu64 dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.41" (uid=1000 pid=4691 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.79" (uid=0 pid=32021 comm="/USR/SBIN/CRON "))
Mar 14 22:30:01 ian-Ubuntu64 dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.41" (uid=1000 pid=4691 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.80" (uid=0 pid=32020 comm="/USR/SBIN/CRON "))
Mar 14 22:30:01 ian-Ubuntu64 CRON[32020]: pam_unix(cron:session): session closed for user root
Mar 14 22:30:01 ian-Ubuntu64 CRON[32021]: pam_unix(cron:session): session closed for user root
```

---

### Post by sandyd on 2010-03-14
> **Bondy_uk said:**
> All I did what a quick selection of the last bits of the files/logs. I tried to copy and paste the entire log twice and it crashed my pc both times :frown:


So is this saying its trying to send emails or something?
```

sudo dpkg --purge --force all nullmailer 
sudo apt-get install postfix
```
dont know what uninstalled nullmailer in the first place... postfix should be used instead of nullmailer

---

### Post by Bondy_uk on 2010-03-14
> **carlee said:**
> ```

sudo dpkg --purge --force all nullmailer 
sudo apt-get install postfix
```
dont know what uninstalled nullmailer in the first place... postfix should be used instead of nullmailer

Thank you, that seems to have done something  :popcorn:

I have no idea what nullmailer or postfix are :confused:
Which option do I need?

1. No configuration
2. Internet site
3. Internet with smarthost
4. Satellite system
5. Local only

---

### Post by Slim Moe on 2010-03-15
Both are mail servers ( kind of .. check Wikipedia for a deeper explanation on both of them ) and if you really didn't knew what they do, you definitely don't need Postfix either.

---

### Post by Bondy_uk on 2010-03-15
> **Slim Moe said:**
> Both are mail servers ( kind of .. check Wikipedia for a deeper explanation on both of them ) and if you really didn't knew what they do, you definitely don't need Postfix either.

No I dont have a clue about nullmailer or postfix. Ive never installed any mail or web server (although Apache seems to be installed and started when I boot for some reason).

It is just a home desktop PC that I do everyday things on (bit of programming, multimedia stuff, Open Office, games, browsing the Internet, etc). Its not like other people were trying to do stuff on it I didnt know about either as there is another PC and laptop for them to use.

Anyway I dont understand why myself, but the Postfix Carlee suggested (with option 1 of no config/keep config) seems to have sorted it :confused:

So thank you everyone for helping! =D>

---

