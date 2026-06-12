---
title: "Two questions about Firestarter and start-up."
date: 2010-08-09
forum: General Help
---

### Post by zozza on 2010-08-09
I have set-up Firestarter to run on start-up using Preferences / Startup Applications. 

However, when I log in, I am informed that since I am not root, I need to load Firestarter manually.  How can I have it automatically start?

Also, once I manually start it, the icon appears in the panel but the program is open.  How can I have it so that it just starts up as an icon in the panel rather than opening fully.

Thanks.

---

### Post by mike555 on 2010-08-09
isn't firestarter just a front end to the firewall that is in Ubuntu? it doesn't need to startup , only time you use it is to change settings ...

---

### Post by ajgreeny on 2010-08-09
Firestarter is apparently not being developed any more, so is probably not the best firewall configuration application to use.  Look at ufw or if you want a gui for it gufw.

In all honesty, you may not need to run a firewall application at all unless you have a need to change any of the default settings of iptables, which is the actual firewall in ubuntu.  I have not had a firewall application in ubuntu for about the last 4 years.  I used firestarter when I began to use ubuntu 5 years ago because coming from windows I assumed that one was necessary, but quickly learned that it was not needed on my system, which has no servers and therefore has no ports open to intruders.

---

### Post by zozza on 2010-08-09
So if you make changes to Firestarter does that mean that iptables automatically reflects these changes and maintains these changes on reboot?

---

### Post by ajgreeny on 2010-08-09
I think so, yes.  However, as I said, I do not change my iptables settings, so can not say for certain.

---

### Post by davidmohammed on 2010-08-09
> **zozza said:**
> So if you make changes to Firestarter does that mean that iptables automatically reflects these changes and maintains these changes on reboot?

yes is the answer to your question.

If you feel doubtful - open up your router (if you are using one) to all incoming traffic (!) - then use [this website]("https://www.grc.com/x/ne.dll?bh0bkyd2") to probe your computer to test for weaknesses in your firewall configuration.

---

### Post by zozza on 2010-08-10
The thing is that I am not using a router.  I am on a University network with a direct static IP (no NAT).  Therefore, I assume that the gateway / firewall blocks negative incoming traffic although not being in control of the gateway / firewall I do not know the policies.  Also, I use Firestarter to prevent potentially negative traffic from going out through limiting ports to http/s, smtp, pop, etc.

---

