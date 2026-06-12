---
title: "XChat and DCC Send on Linksys router"
date: 2005-02-15
forum: General Help
---

### Post by delltony on 2005-02-15
I have searched high and low and still not found a workable solution for the following issue.  
Problem: I can not dcc send files to anyone on irc. 
What has been tried:
 [list=1]
[*]added 1024 to 65535 port forwarding on router to 192.168.1.200
[*]Added 1023 as the first port and 65535 as the last port in xchat dcc options
[*]Turned on Get ip from irc server in dcc options
[*]did a nmap -T5 on my real ip to show ports 1023 to 65535 successful
[*]Tried to send file to friend and did a netstat -tlnp and showed xchat listening on port 1024
[/list] 

I have no idea what to try next i can receive files all day long of course but I can not send, the person sees the file but ack flag never seems to be sent.

help on this would be great. I tried #xchat on freenode but nothing seemed to resolve the problem. Thanks in advance and above all thanks Ubuntu to making linux a little easier to use

update: Problem resolved
Solution: added Ip to field manual in xchat settings and it works great.

---

