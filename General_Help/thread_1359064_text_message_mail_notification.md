---
title: "text message mail notification"
date: 2009-12-19
forum: General Help
---

### Post by eppo on 2009-12-19
i'm setting up a mail server. what i'm looking to do is have the server send a text message notification to my cell phone when mail arrives. is there an application that already does such a thing, or a simple shell script that i could write to do it?
thanks

---

### Post by HermanAB on 2009-12-19
The problem is that each cell provider has a different SMS gateway.  You have to figure it out yourself, but there is some help on Wikipedia:
[http://en.wikipedia.org/wiki/SMS_gateway](http://en.wikipedia.org/wiki/SMS_gateway)

---

### Post by joes7 on 2009-12-19
There are some solutions online, I have seen them before, and they are quite good.

---

### Post by LostDakota on 2010-01-11
I'm sure you got something working, but I figured I'd offer another solution. You could create a Facebook or Twitter account for your server. Look up [fbcmd]("http://fbcmd.dtompkins.com/") (for FB) and curl (for T). Essentially, you friend yourself and allow SMS notifications. fbcmd allows you to use the command line to check your friends status and update your own. Once you have that in place, you just configure fbcmd to use the server's account. The last step would be to write a script and put it in your crontab so it runs every minute (* * * * *).  I use this for checking unauthorized SSH attempts. Ex.

```
#!/bin/bash

LOG=/var/log/auth.log
FB=/home/drew/fbcmd/fbcmd.php

cat $LOG | tail -n 20 | grep -q Failed && php $FB STATUS "Check Server Logs Failed login attempt."

``` 

Hope that helps someone.

---

