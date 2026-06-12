---
title: "Firestarter Question"
date: 2009-11-22
forum: General Help
---

### Post by n_s_simpson on 2009-11-22
Hi

I'm using Firestarter and have a few questions I'm struggling to find answers for:

1) when first booting Ubuntu the Firestarter icon is not there. What state is it in (active or disabled)

2) when i change the status from active to disabled my psp can't find a DNS server. I thought disabled allowed everything to get full access. My actual PC can still get on the web okay.

---

### Post by MichiganMan on 2009-11-22
First question is easy.  The firewall, aka iptables, is in the state that you set it the last time you ran Firestarter.  This is true whether Firestarter is active or not.  Firestarter only configures iptables, which I understand is otherwise a formidable task when done directly.

Swing by [GRC]("http://www.grc.com/") and use his Shields Up port scanner to test the firewall.  Obviously if you have a router between you and the net than make sure you're not scanning that.  

Can't help you with the second question.  Sorry.

---

### Post by n_s_simpson on 2009-11-22
Hi MichiganMan

Thanks for the reply. Yeah I tried ShieldsUp and everything is working.

Just can't understand why when I use ICS the DNS fails to work when Firestarter is set to disabled. I'm sure this wasn't the case when I ran Firestarter in 9.0.4 before I did the upgrade.

P.S.

I don't currently have broadband in my new house so I'm using my phone to connect. I have a WiFi router set up to be an access point.

---

### Post by n_s_simpson on 2009-11-23
Does anyone else have any idea why setting the Firestarter status to disabled stops devices from seeing the DNS server?

---

### Post by n_s_simpson on 2009-11-28
Looks like I'm getting broadband installed in a couple of weeks so this isn't as important but I'd still like to know just out of interest.

---

### Post by QLee on 2009-11-28
Well, you use Firestarter to do the ICS for your network, eh? It seems to me that disabling the application that does the ICS might reasonably stop it from working. Your LAN clients try to connect to a service for DNS that has been turned off.

---

