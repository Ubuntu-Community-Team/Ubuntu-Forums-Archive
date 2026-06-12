---
title: "VPN - Proxy - Firewall - AV"
date: 2010-02-01
forum: General Help
---

### Post by jebi on 2010-02-01
hi
 
i am looking to make ubuntu my main OS but i want to make it more internet safe just a question about 3 things really... please keep it simple im a noob to linux...
 
1. does anyone know how to set up a free secure VPN and / or proxy i looked in synaptic package installer but did not really find anything? (need something that would find the free proxies for me)
 
2. what are the best free firewalls idealy one that gives a yes/no to programs before they start accessing the internet?
 
3. and what is the best free AV for ubuntu or linux in general?
 
thx any help appreciated
 
jebi

---

### Post by t4thfavor on 2010-02-01
1. you have to have an endpoint to terminate a vpn, as for a proxy, I'm not sure you even need that to be secure. Do you mean anonymous?

2. Iptables is built into Linux, you just need a program to control it so you don't have to learn all the cryptic commands. I recomend firestarter, or guarddog/guidedog If want to set it to be default deny for traffic it will be a headache, but doable. You probably already have a firewall, if you have a separate internet router, so it's probably not all that nessecery.

3. ClamAV, kapersky, and BitDefender. I like BitDefender, but it is not free. Unless you have Windows machines you want to protect, you don't need this, as your chances of getting a virus on Linux are very very small.

Good luck, let us know how it goes.

---

### Post by bodhi.zazen on 2010-02-01
I think you should start with this sticky :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

I think most of what you want in a VPN are features of a router. Most routers have firewalls in them as well. If you like you can build a router, all it takes is an old box with 2 netwrok cards.

What do you want a proxy for exactly ?

What do you want to do with a firewall ? A default installation of Ubuntu (unlike Windows) has no listening servers, and assuming you use a router, adding a firewall to your desktop is redundant redundant.

IMO the best "free" AV is to not run AV at all. Considering that there are no know active viruses (you system was patched for the know viruses long long ago) there is nothing to scan for.

Did I mention you should probably start here : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")  

Linux is not windows and likewise much of what you are asking probably does not apply.

---

