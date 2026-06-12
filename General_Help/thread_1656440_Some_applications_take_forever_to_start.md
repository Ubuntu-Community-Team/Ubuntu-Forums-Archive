---
title: "Some applications take forever to start"
date: 2010-12-30
forum: General Help
---

### Post by woooinred on 2010-12-30
Hi,

I have been having this issue since 2 days ago. Basically everytime I starts firefox or gvim, it takes few minutes to start. And even if the app started, it will randomly stop running for up to few minutes then continue to work again. For both applications, I noticed if I disconnect the system from LAN, the issue is gone. I have googled a bit and tried disabling IPV6, modifying /etc/host with no luck. I also tried to do an apt-get upgrade, and clean OS install but still can't get the issue resolved. I would like to ask for help here before I go further and build a debug version of firefox and see what actually stops it from starting/running. 
Some system info that I hope will help:
1. Ubuntu 8.04.1 hardy kernel 2.6.24
2. Xorg 1.4
3. LPIA architecture platform

PS. Firefox worked perfectly until I noticed the issue two days ago and I don't remember making any significant modification to the system that could cause the problem.

---

### Post by dcstar on 2010-12-31
> **woooinred said:**
> Hi,

I have been having this issue since 2 days ago. Basically everytime I starts firefox or gvim, it takes few minutes to start. And even if the app started, it will randomly stop running for up to few minutes then continue to work again. For both applications, I noticed if I disconnect the system from LAN, the issue is gone.
.........

Check your DNS settings, you probably have a bad server listed.

---

### Post by woooinred on 2010-12-31
> **dcstar said:**
> Check your DNS settings, you probably have a bad server listed.

dcstar, sorry I am a noob on DNS stuff. How am I supposed to tell if the serach/name servers listed are bad? By the way, I probably should've mentioned Opera is working fine and there's no problem for me to use Opera to browse internet (doesn't this tell me the DNS is good?).

---

