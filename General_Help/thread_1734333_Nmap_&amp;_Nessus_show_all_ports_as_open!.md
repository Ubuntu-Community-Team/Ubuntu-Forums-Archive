---
title: "Nmap &amp; Nessus show all ports as open!"
date: 2011-04-20
forum: General Help
---

### Post by yaru on 2011-04-20
Hi all, my first post here.
I have picked up pentesting as my last-year project at uni and I have a client there connected to uni's network with official permission for pentesting. I use Backtrack 4 R2 on VMwrae (Bridged connection) for this purpose but I have a big problem with Nmap and Nessus I thought I'd ask about here. (Yeah, I know this is not Nmap or Backtrack forum but Nmap doesn't have an official forum and I'm afraid Bakctrack's forum is far from active and the people back there are less than helpful.:( )

My problem is that whenever I scan any IP with either Nmap or Nessus, either outside or inside uni's network, either from Backtrack in VMware or from the XP OS I have installed VMware on, they report every single port, without exception, as open. Although I have noticed few situations in which Nmap randomly reports a few ports as closed (not unreachable). Though there is an exception to this pattern, if I scan the clients that are connected to the same switch as the client I use, Nmap and Nessus give me the right results!!

I even made a copy of my Backtrack installation on VMware and brought it home and ran it (on Vmware) and scanned the same IPs, the results are completely correct at home.

I am nearly sure that some kind of a firewall or IDS on uni's network is causing this and I have already reported this (more like complained about it. :D) to my uni's officials but since those people don't seem to be that sure about what they're doing and have no obligation to attend to my problem, I thought I'd ask for help elsewhere so that I'd be able to sort this issue asap, I don't have an infinite amount of time for my project, you know, so any help in this matter is really appreciated.

P.S. I would have been more than happy to take care of all these at home but because of some connections problems I have atm (long story short, I'm on dial-up at home), I can't, and have to do it at uni.

Edit: Forgot to say this, this problem applies to all of Nmap's TCP scans, the UDP scan works just fine on all IPs (outside and inside uni).

---

