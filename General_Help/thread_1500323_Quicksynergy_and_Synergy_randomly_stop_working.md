---
title: "Quicksynergy and Synergy randomly stop working"
date: 2010-06-03
forum: General Help
---

### Post by kyleabaker on 2010-06-03
I'm using Quicksynergy on my desktop (Ubuntu 10.04) computer as the server and Synergy on my Laptop (Windows XP) which is right beside my desktop.

Everything works well for a while, but randomly seems to stop working. When I look into the problem, it seems that its with Quicksynergy on my desktop.

I find that I have to quit Quicksynergy and open the system resources application to kill the Synergy daemon (or whatever it is) that Quicksynergy uses.

Restarting Quicksynergy after killing the daemon fixes the problem as my laptop always reconnects perfectly fine.

Does anyone else have this problem in Ubuntu? I'd like to get this fixed so I don't have to keep killing the synergy process and restarting Synergy. I used to be able to get great uptime with this setup, but not anymore.

---

### Post by jcapinc on 2010-11-01
I am having the same problem, only I can just stop and re-start the services on both computers and it keeps going just fine.  It happens almost every hour for me, very annoying.

Anyone know why it would be doing this?

---

### Post by spyd4r on 2010-11-30
I have the same issue, no fix yet other than killing and restarting the client

---

### Post by drewsus on 2010-11-30
I stopped using quicksynergy, went for synergy+ and did the conf manually. Also, do you run the client using the netbios name or ip address? I found using the ip address to be more reliable.

---

### Post by spyd4r on 2010-11-30
> **drewsus said:**
> I stopped using quicksynergy, went for synergy+ and did the conf manually. Also, do you run the client using the netbios name or ip address? I found using the ip address to be more reliable.

I use Synergy+ 1.3.5 on windows and connect via IP.

---

### Post by Ronin_301 on 2010-12-03
I've been having the same problem with the syngery server running on my Ubuntu 10.04 desktop, and the client running on a laptop dual booting Win7 and Ubuntu 10.10 (both running the client). The server stops responding until I kill it and restart. It's only been going on for a couple days.

---

