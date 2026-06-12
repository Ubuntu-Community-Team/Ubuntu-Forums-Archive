---
title: "ssh keeps dropping"
date: 2006-06-15
forum: General Help
---

### Post by lex1 on 2006-06-15
Hi

Everytime I boot up it says ssh is running but if someone try;s to connect they cannot
so i remove and install openssh-server again and its ok for a few hours then it drops?

I am useing fluxbox on a labtop.
ssh on port 22 (tcp6)

any feedback would be a great help.

lex1:rolleyes:

---

### Post by Ramses de Norre on 2006-06-15
Firewall or router? 
Port 22 should be open for at least the host the other person is connecting from and should be forwarded to your local ip from your router if you have one.

---

### Post by lex1 on 2006-06-15
It is a router and port 22 is open.

lex1

---

### Post by scxtt on 2006-06-15
check "/var/log/auth.log" and see if ssh(d) is giving any error messages ...

---

### Post by lex1 on 2006-06-15
looked /var/log/auth.log but no errors
tried to connect on port 22 from remote machine 3 hours after booting could connect ok.

however after 6.5 hours tried again could not connect connection timed out.


lex1

---

### Post by scxtt on 2006-06-16
looking in my auth.log i see some:

[indent]"Jun 12 01:45:56 localhost sshd[4731]: Received signal 15; terminating."[/indent]

but they are followed by:

[indent]"Jun 15 04:51:38 localhost sshd[4728]: Server listening on :: port 22."[/indent]

not immediately, but i was using SSH for 8 hours today and wasn't disconnected once ... and it was up since:

[indent]"Jun 15 05:29:58 localhost sshd[5982]: Server listening on :: port 22."[/indent]

---

### Post by lex1 on 2006-06-16
i do not understand your reply.

Yesterday I turned thelabtop off once.

is the auth.log ok?


lex1

---

### Post by scxtt on 2006-06-16
the "signal 15" is bad, means sshd is being shutdown (i have this message as well, but it doesn't happen after a certain amount of time - i was logged into my computer from work for 8 hours straight) ... the "Server listening on :: port 22" is the reconnect, which is in your log as well so it doesn't seem like your daemon is having a problem (or doing anything too out of the ordinary) ... what i would recommend is to take a look in the auth.log IMMEDIATELY after a connection is dropped and see if you see the "signal 15" and how long it takes for the "Server listening ..." message to appear ... maybe your sshd is being superceded by something else?

---

### Post by lex1 on 2006-06-16
Thanks for your post


you said

"i would recommend is to take a look in the auth.log IMMEDIATELY after a connection is dropped "

how do i know when a connection has dropped all i do is try to connect from time to time one time its connected the next time it times out i do not know which time you are refereing to?


lex1

---

### Post by scxtt on 2006-06-16
if your connection isn't dropping when you're currently connected via ssh, do something like this:

1. boot up your box
2. take a look @ auth.log and note the LAST instance of SSH being up { "Server listening on :: port 22." } and what time it happened ...
3. note the time that you try to connect and can't and we'll try and figure out what's happening b/t those two times ...

i know we have some output from your auth.log, but that hasn't narrowed it down - because i have similar entries in my auth.log - but i'm not experiencing the issue like you are ...

also, where are you trying to connect from (local network, or outside IP)?  and does your ISP ever have connection issues, is your router reliable?

---

### Post by lex1 on 2006-06-16
My router is pretty good.

on issues that I know of.

I have adsl 24/7 with a static ip address with a reverse DNS.

Lex1
ps i will do as you sugested
sent 2 pm's entitled

---

### Post by lex1 on 2006-06-17
seems to be a problem with when not active on labtop

---

