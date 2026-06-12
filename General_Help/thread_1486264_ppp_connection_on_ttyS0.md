---
title: "ppp connection on ttyS0"
date: 2010-05-17
forum: General Help
---

### Post by BigMamma on 2010-05-17
I'm using Hardy and am having trouble with a ppp connection on ttyS0. I'm using pon with my own peer. My peer in /etc/ppp/peers is:
/dev/ttyS0
19200
demand
idle 60
connect /etc/ppp/chatScr.sh
90.0.0.2:90.0.0.1
user NeverAuthenticate
 
chatScr.sh is:
#!/bin/sh
/usr/sbin/chat -v -f /etc/ppp/myChat.linux
 
myChat.linux is:
"" CLIENT\c
SERVER
 
/etc/ppp/options is:
noauth
nodefaultroute
nocrtscts
local
noproxyarp
debug
 
Using plog, I see that the connect script is always failing. Using pppstats indicates nothing is being sent or received. ttyS0 looks okay in setserial (I think).
 
Luckily, my host has a removable hard drive. When I remove the Hardy disk and use my Solaris 10 x86 disk (without touching any h/w) the connection works properly and the device on the other end of my serial cable responds correctly. The only difference with the Solaris configuration is that it has a 'noident' option as well as those above.
 
Please help me; I'm stuck. Thanx,

---

### Post by BigMamma on 2010-05-21
I was able to solve this problem by putting the whole chat script in the peer description instead of calling a separate shell script.

---

