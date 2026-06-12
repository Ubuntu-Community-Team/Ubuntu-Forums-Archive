---
title: "how to remove P2P software"
date: 2011-08-03
forum: General Help
---

### Post by charlescva on 2011-08-03
I am running Ubuntu 11.04

I have been using ubuntu for over a year and as of July 31st my Company's Corporate IT department has sent me a notification that my PC is running p2p software.  I have looked in synaptic and do not see anything installed since then that could be the culprit.

I am familiar with torrent software like azure and uTorrent.  I am not using these type of tools and they are not installed.

I was wondering if i could analyze my traffic and determine what port the requests are going out on... then maybe determine a process ID from the port number? I really don't want to "format" my pc and switch back to windows, but if i cant get this p2p software off, i will have to.

thanks in advance,

charles

---

### Post by CatKiller on 2011-08-03
Sounds like a false positive to me.

---

### Post by thefasterblueone on 2011-08-03
Run this command in Terminal to show current internet connections:

```
lsof -i -n -P
```


or you could install NetHogs to show connections continually, "live".

NetHogs can be found in the Ubuntu Software Center.

---

### Post by pqwoerituytrueiwoq on 2011-08-03
the only one that is in ubuntu by default is transmission (for torrent files)
they either don't want you eating all they band width or are assuming you are using something like limewire and dont want there network compromised with viruses could be both though

anyone know if emapathy counts if you are using the people nearby account?

---

### Post by charlescva on 2011-08-03
> **CatKiller said:**
> Sounds like a false positive to me.

could be.... ive noticed A LOT of tickets floating around this week about people using "unauthorized" services on their PC...Corporate IT up to their usual tricks...  Nothing worse then being forced to use Windows XP and 100+ processes on a Core i7 w/ 8GB RAM because the new windows 7 image isn't loaded with their malware yet.

---

### Post by charlescva on 2011-08-03
> **thefasterblueone said:**
> Run this command in Terminal to show current internet connections:

```
lsof -i -n -P
```


or you could install NetHogs to show connections continually, "live".

NetHogs can be found in the Ubuntu Software Center.

Thanks, This was really helpful! 

The command shows that currently skype, pidgin and Firefox have connections.  

Corporate Ticket said that on july 31st at 16:00ish EST a request went out from my pc and several hundred PCs responded back from the public domain and were blocked.  LOL... that is all... no other information is given.

Perhaps this is something I will have to continually monitor.

---

### Post by pqwoerituytrueiwoq on 2011-08-03
that sounds like a boradcast to me (something sent to x.x.x.255)

---

### Post by charlescva on 2011-08-03
> **pqwoerituytrueiwoq said:**
> that sounds like a boradcast to me (something sent to x.x.x.255)

Yea, I didnt see anything currently running...but it doesnt mean that it wont try again.

I have implemented "Firestarter" as a firewall and hope that it will block any broadcasts in the future

I have it set to block broadcasts from both internal and external networks.... however i feel as though this firewall software may not be what i am looking for.

Do you think this will adequately block my PC from sending out these broadcasts in the future? how would I test this firewall? as i see pidgin, skype and firefox are showing up in the "active connections" of firestarter, but i never authorized them to continue working.

Guess im sort of looking for a firewall solution similar to that of Windows, where I am alerted and manually choose what to allow.  Any ideas?

---

### Post by charlescva on 2011-08-03
Got it working...

So I got the firewall working correctly and currently am only allowing HTTP on port 80. Inbound/outbound...

I will have to update my policy regularly... but this is a good start for keeping a grip on what my PC is doing.

Thank you all for your help.


PS.

Firewall really adds the delay on to each request. Oh well...

---

### Post by pqwoerituytrueiwoq on 2011-08-03
try the firewall configuration that one is just a gui for the existing firewall software

---

### Post by charlescva on 2011-08-03
Guess it was Skype, as it says P2P connect failed, now.

---

