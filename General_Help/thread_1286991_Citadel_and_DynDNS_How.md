---
title: "Citadel and DynDNS: How?"
date: 2009-10-09
forum: General Help
---

### Post by nuseryame on 2009-10-09
I'm just playing around with Citadel mail server but don't know how it works.

I have a wireless router, behind that is my main PC 192.168.1.2, and on this PC in VirtualBox I have Xbuntu 192.168.1.3 which contains the Citadel mail server.

I have registered my free domain name at DynDns and inserted it in Citadel but I'm not sure what to do next to get it to work.

What settings do I need to change for my router? because if someone types mail.dyndns.org which points to my WAN IP, how do they get to my LAN IP 192.168.1.3 which contains my mail server?

Is there a setting that says, if request from mail.dyndns.org then forward to 192.168.1.3?

---

### Post by nuseryame on 2009-10-09
Ok I just removed all security from my router, enabled port forwarding and put it in the DMZ and I was able to receive email from hotmail but sending it never worked.

I've secured everything now. It must be the case that if you want to access your home server from the internet, you need to put it in the demilitarized zone, which has no security. You probably need to have a dedicated hardware firewall and dedicated mail server for protection.

---

### Post by steev182 on 2009-10-09
You may be with an ISP that doesn't allow port 25 outbound. That would explain why you can receive email but not send it.

---

### Post by CharlesA on 2009-10-09
> **nuseryame said:**
> 
Is there a setting that says, if request from mail.dyndns.org then forward to 192.168.1.3?

Sitting any machine in the DMZ is a bad idea, you can just forward the port the mail server uses in the router config.

What brand of router do you have?

---

### Post by nuseryame on 2009-10-09
Ok I just needed to port forward the appropriate mail ports.

However, how come when I enter my dyndns domain in a browser it never takes me to the Citadel webmail login? I forwarded port 80 and 443 to my mail server.

---

### Post by nuseryame on 2009-10-09
I can access my webmail if I remove www and just type the domain name on its own.

---

### Post by caseygibbs on 2010-01-10
Ever get this working? I have a similar situation. Ubuntu, with Ubuntu Server inside a VBox vm, with bridged networking to my wireless router and all necessary ports forwarded. I have purchased MailHop Outbound from dyndns.com, which lets you use their smtp address for outgoing mail, but when I put it in my smart hosts, I still can't get mail out. Dyndns suggests using port 2525 if your ISP blocks 25 for outgoing, so I changed that port assignment in Citadel's site-wide config page and restarted; still no good. Nearing my wit's end :)
C

---

### Post by caseygibbs on 2010-02-07
I don't know if you're still working on this but I got it up and running beautifully and can't believe I ever fiddled around with anything else. Citadel rocks.

---

