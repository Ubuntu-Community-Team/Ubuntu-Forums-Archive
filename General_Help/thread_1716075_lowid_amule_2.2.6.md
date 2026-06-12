---
title: "lowid amule 2.2.6"
date: 2011-03-27
forum: General Help
---

### Post by bitbomb on 2011-03-27
I give up.

I installed amule 2.2.6  I forwarded ports 4662, 4665, and 4672 and I keep getting lowid everytime I start amule.  I scanned my external IP address with nmap

**TCP scan**
nmap -sT -p 4662,4665,4672 <external IP here>
4662/tcp open   edonkey
4665/tcp closed unknown
4672/tcp closed rfa

**UDP scan**
nmap -sU -p 4662,4665,4672 <external IP here>
4662/udp closed          unknown
4665/udp open|filtered unknown
4672/udp open|filtered rfa

The ports are open. Still I have lowid.   What am I doing wrong?

---

### Post by bitbomb on 2011-03-29
Finally got it to work.

I cloned my mac address in order to force my ISP to reissue me a new IP  address.  When I restarted aMule I got HighID!  I'm not sure why that  worked.  Finally!!

---

### Post by incognita on 2011-11-27
> **bitbomb said:**
> Finally got it to work.

I cloned my mac address in order to force my ISP to reissue me a new IP  address.  When I restarted aMule I got HighID!  I'm not sure why that  worked.  Finally!!

Hi! I am having the same problem, like so many others. Would really appreciate it if you tell what exactly you did with the cloning of the mac address. Maybe a little detailed in the instructions? Thanks!

---

