---
title: "Running 317 rsps client"
date: 2010-06-26
forum: General Help
---

### Post by Simdog1 on 2010-06-26
well i got ubuntu aabout a month ago and ive been trying to play games  but none of them work for me then i remebered about rsps and used the  ubuntu forum to get help with the 508 servers. (which work for me new if  u need help i think i can help or post a lonk on how to get the 508  server working on ubuntu) but now i wanna try 317 servers the client  loads which isnt my problem but then when i get in game there are  invisible people (i see them on minimap) and when i do 1 move the client  crashes. here is the error it get.
hs_err_pid2288.log
#
# A  fatal error has been detected by the Java Runtime Environment:
#
#   SIGSEGV (0xb) at pc=0x00007fb8680f3f19, pid=2288, tid=140429507319568
#
#  JRE version: 6.0_20-b02
# Java VM: Java HotSpot(TM) 64-Bit Server VM  (16.3-b01 mixed mode linux-amd64 )
# Problematic frame:
# V   [libjvm.so+0x1dcf19]
#
# If you would like to submit a bug report,  please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

(i  only put some of it if i put it all it would be too long) 
if you  know why i crash please help o and here is how i cnahged it to make  client run

Before:
@echo off

title Extreme-Pkz Client

java  -Xmx300m Jframe 10 0 highmem members 32

pause

After:
#!/bin/bash
title  Extreme-Pkz Client
echo "off"
java -Xmx300m Jframe 10 0 highmem  members 32
pause

please help thanks

---

### Post by Simdog1 on 2010-06-26
Bump please help. wow this went down fast

---

### Post by Simdog1 on 2010-06-26
bump

---

### Post by Simdog1 on 2010-06-29
^^^^^

---

### Post by Simdog1 on 2010-07-05
bumpity

---

### Post by bobz1993 on 2010-09-12
this has something to do with being on a 64-bit system apparently...
i'm just getting back into rsps and i was going to test my server from my laptop win7x64 after 2 clicks i got an error like that...
ironically like 5 minutes earlier i pass by a thread on rune-server about this exact problem... i'm waiting for a reply on this myself as the info in the thread didn't work for me...
[http://www.rune-server.org/runescape-development/rs2-client/tutorials/263550-running-client-64-bit-noob-friendly.html](http://www.rune-server.org/runescape-development/rs2-client/tutorials/263550-running-client-64-bit-noob-friendly.html)
if you're still interested...

---

