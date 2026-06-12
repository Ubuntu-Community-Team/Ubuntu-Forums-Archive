---
title: "Monitor ports"
date: 2006-04-09
forum: General Help
---

### Post by flebber on 2006-04-09
How can I monitor my ports to know what I am using or to determine what is using a port.
I was trying to use kmldonkey and it said cannot open as port 4662 is in use, so I shut frostwire down and though that would resolve it. whats the best and safest way to lookup up ports in use? 

The exact error message that mldonkey core gave me was :
> 2006/04/09 14:58:29 Starting MLDonkey 2.7.1 ... 
2006/04/09 14:58:29 Language EN, locale UTF-8
2006/04/09 14:58:29 MLDonkey is working in .
2006/04/09 14:58:29 [DNS] Resolving [ubuntu] ...
2006/04/09 14:58:29 [DNS] Resolving [[www.mldonkey.net]](www.mldonkey.net]) ...
2006/04/09 14:58:29 [IPblock] loading ./guarding.p2p
2006/04/09 14:58:29 [IPblock] file ./guarding.p2p not found
2006/04/09 14:58:29 [cCO] Options correctly saved
2006/04/09 14:58:29 Check [http://www.mldonkey.net/](http://www.mldonkey.net/) for updates
2006/04/09 14:58:29 enabling networks: 
Exception: bind failed: Address already in use at port 4662
This is normally caused by another application currently using this port.
Close that application and restart MLDonkey, exiting...

---

### Post by nanotube on 2006-04-09
use command "netstat" to see what ports are open. the following command line switches are a good start:
```
netstat --tcp -p -a
```
give that a shot from a terminal and see what comes up. :)

---

### Post by flebber on 2006-04-09
Interestingly its itself that has the port
> PID/Program name
tcp        0      0 *:4000                  *:*                     LISTEN     7
461/mlnet
tcp        0      0 *:4001                  *:*                     LISTEN     7
461/mlnet
tcp        0      0 *:6881                  *:*                     LISTEN     7
461/mlnet
tcp        0      0 *:4002                  *:*                     LISTEN     7
461/mlnet
tcp        0      0 *:6882                  *:*                     LISTEN     7
461/mlnet
tcp        0      0 *:11491                 *:*                     LISTEN     7
461/mlnet
tcp        0      0 localhost.localdom:2149 *:*                     LISTEN     -

tcp        0      0 *:4080                  *:*                     LISTEN     7
461/mlnet
tcp        0      0 *:4662                  *:*                     LISTEN     7
461/mlnet


---

### Post by nanotube on 2006-04-10
interestingly indeed. :)
seems like some kind of bug in mlnet, i guess...

---

### Post by flebber on 2006-04-10
I removed every instance of mldonkey and mlnet and re-installed. Now Kmldonkey starts ok and connects to core However I find myself without it having any servers in its server list.

---

### Post by nanotube on 2006-04-11
heh well, i dont know anything about the ml programs per se, so can't help you on this one...

---

