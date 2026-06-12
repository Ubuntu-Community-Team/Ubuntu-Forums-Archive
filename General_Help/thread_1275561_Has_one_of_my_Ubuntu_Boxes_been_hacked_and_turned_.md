---
title: "Has one of my Ubuntu Boxes been hacked and turned into a bot?"
date: 2009-09-26
forum: General Help
---

### Post by Razmear on 2009-09-26
Howdy, 
I'm not an expert and I'm seeing some strange things so here I am asking for help. 
I have 2 Ubuntu boxes on a home network hooked up to AT&T DSL service. 
They are connected via a simple 5 port switch which goes to the DSL modem. 
I just recently got Vonage, and plugged that into the switch as well. 

I don't know if this is a new problem since the Vonage box was installed, or if just the box flashing everytime the internet connection resets is letting me know there is a problem. I stream video alot, so I think I would have noticed the frequent lockups before as my internet is being reset every hour or less. 

I checked my DSL Modems logs and found this: 

```

SAT SEP 26 03:47:59 2009 DNS: Unknown host: '70562.cim.meebo.com.launchmodem.com'

SAT SEP 26 03:47:53 2009 PPP CONNECTED on VPI 8 VCI 35

SAT SEP 26 03:47:53 2009 Connecting session(0): My Connection due to dsl Restart

SAT SEP 26 03:46:58 2009 LAN PC unable to communicate with DNS Server.(error = 'connection timed out', count=3)

SAT SEP 26 03:46:55 2009 LAN PC unable to communicate with DNS Server.(error = 'connection timed out', count=3)

SAT SEP 26 03:46:55 2009 PPP DISCONNECTED on VPI 8 VCI 35 : PPP commanded down

SAT SEP 26 03:46:55 2009 Disconnecting session(0): My Connection due to dsl Restart

SAT SEP 26 03:44:22 2009 DNS: Unknown host: '29.97.211.95.sbl.spamhaus.org'

SAT SEP 26 03:44:22 2009 DNS: Unknown host: '206.85.211.95.sbl.spamhaus.org'

SAT SEP 26 03:44:20 2009 DNS: Unknown host: '34.97.211.95.iadb.isipp.com'

SAT SEP 26 03:44:20 2009 DNS: Unknown host: '34.97.211.95.sa-trusted.bondedsender.org'

SAT SEP 26 03:44:20 2009 DNS: Unknown host: 'freecashcyber.com.fulldom.rfc-ignorant.org'

SAT SEP 26 03:44:20 2009 DNS: Unknown host: '34.97.211.95.sa-accredit.habeas.com'

SAT SEP 26 03:44:20 2009 DNS: Unknown host: '34.97.211.95.list.dnswl.org'

SAT SEP 26 03:44:20 2009 DNS: Unknown host: '34.97.211.95.dnsbl.sorbs.net'

SAT SEP 26 03:44:20 2009 DNS: Unknown host: '34.97.211.95.zen.spamhaus.org'

SAT SEP 26 03:44:20 2009 DNS: Unknown host: 'freecashcyber.com.bl.open-whois.org'

SAT SEP 26 03:44:19 2009 DNS: Unknown host: 'freecashcyber.com.rhsbl.ahbl.org'

SAT SEP 26 03:44:19 2009 DNS: Unknown host: 'freecashcyber.com.dob.sibl.support-intelligence.net'

SAT SEP 26 03:44:19 2009 DNS: Unknown host: '34.97.211.95.bl.spamcop.net'

SAT SEP 26 03:44:19 2009 DNS: Unknown host: '34.97.211.95.combined.njabl.org'

```

The unknown host errors continue on for quite a bit longer.

Now I am obviously not trying to connect to any of these sites, and there might be more hosts that are not unknown that are not showing up in the logs, so the question is why are these sites trying to be loaded to the point where it apparently crashes my DSL modem?

The only new item on the network is this Vonage box, so I'm also curious if it can be hacked or have some other issue that is tripping the DSL modem. 

I can provide whatever other logs or config files you might want to see, but I really don't know where to start looking. 

Thanks,
eb

---

### Post by Razmear on 2009-09-26
Quick update, I unplugged the Vonage box from the 5 port hub and I'm not longer getting the DSL disconnects, but still getting the strange addresses in the log. 
Now I'm wondering if the log entries could be related to SpamAssasin? 

Latest batch: Note the 3 minute gap, then all the remaining entries occur within the same minute.
```

SAT SEP 26 04:59:49 2009 DNS: Unknown host: 'bedcircle.com'

SAT SEP 26 04:59:21 2009 DNS: Unknown host: '39.49.110.210.iadb.isipp.com'

SAT SEP 26 04:59:20 2009 DNS: Unknown host: 'buende.com.fulldom.rfc-ignorant.org'

SAT SEP 26 04:59:20 2009 DNS: Unknown host: '39.49.110.210.list.dnswl.org'

SAT SEP 26 04:59:20 2009 DNS: Unknown host: '39.49.110.210.zen.spamhaus.org'

SAT SEP 26 04:59:20 2009 DNS: Unknown host: '39.49.110.210.sa-trusted.bondedsender.org'

SAT SEP 26 04:59:20 2009 DNS: Unknown host: '39.49.110.210.sa-accredit.habeas.com'

SAT SEP 26 04:59:20 2009 DNS: Unknown host: 'buende.com.bl.open-whois.org'

SAT SEP 26 04:59:19 2009 DNS: Unknown host: 'buende.com.rhsbl.ahbl.org'

SAT SEP 26 04:59:19 2009 DNS: Unknown host: 'bedcircle.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:59:19 2009 DNS: Unknown host: '39.49.110.210.combined.njabl.org'

SAT SEP 26 04:59:19 2009 DNS: Unknown host: '39.49.110.210.plus.bondedsender.org'

SAT SEP 26 04:59:19 2009 DNS: Unknown host: 'bedcircle.com.bl.open-whois.org'

SAT SEP 26 04:56:49 2009 DNS: Unknown host: '202.11.164.63.sbl.spamhaus.org'

SAT SEP 26 04:56:48 2009 DNS: Unknown host: '10.34.239.216.sbl.spamhaus.org'

SAT SEP 26 04:56:46 2009 DNS: Unknown host: '2.127.80.208.sbl.spamhaus.org'

SAT SEP 26 04:56:46 2009 DNS: Unknown host: '2.124.80.208.sbl.spamhaus.org'

SAT SEP 26 04:56:46 2009 DNS: Unknown host: '8.190.178.205.sbl.spamhaus.org'

SAT SEP 26 04:56:46 2009 DNS: Unknown host: '221.10.96.208.sbl.spamhaus.org'

SAT SEP 26 04:56:45 2009 DNS: Unknown host: '2.126.80.208.sbl.spamhaus.org'

SAT SEP 26 04:56:45 2009 DNS: Unknown host: '105.128.191.199.sbl.spamhaus.org'

SAT SEP 26 04:56:45 2009 DNS: Unknown host: '2.148.94.208.sbl.spamhaus.org'

SAT SEP 26 04:56:45 2009 DNS: Unknown host: '8.144.178.205.sbl.spamhaus.org'

SAT SEP 26 04:56:45 2009 DNS: Unknown host: '221.209.28.66.sbl.spamhaus.org'

SAT SEP 26 04:56:45 2009 DNS: Unknown host: '42.231.240.66.sbl.spamhaus.org'

SAT SEP 26 04:56:45 2009 DNS: Unknown host: '68.106.9.72.sbl.spamhaus.org'

SAT SEP 26 04:56:45 2009 DNS: Unknown host: '220.209.28.66.sbl.spamhaus.org'

SAT SEP 26 04:56:44 2009 DNS: Unknown host: '9.178.9.204.sbl.spamhaus.org'

SAT SEP 26 04:56:44 2009 DNS: Unknown host: '2.125.80.208.sbl.spamhaus.org'

SAT SEP 26 04:56:44 2009 DNS: Unknown host: '69.16.127.12.sbl.spamhaus.org'

SAT SEP 26 04:56:44 2009 DNS: Unknown host: '4.16.89.69.sbl.spamhaus.org'

SAT SEP 26 04:56:44 2009 DNS: Unknown host: '165.162.109.208.sbl.spamhaus.org'

SAT SEP 26 04:56:44 2009 DNS: Unknown host: '10.32.239.216.sbl.spamhaus.org'

SAT SEP 26 04:56:44 2009 DNS: Unknown host: '10.9.222.67.sbl.spamhaus.org'

SAT SEP 26 04:56:44 2009 DNS: Unknown host: '106.128.191.199.sbl.spamhaus.org'

SAT SEP 26 04:56:43 2009 DNS: Unknown host: '201.11.164.63.sbl.spamhaus.org'

SAT SEP 26 04:56:43 2009 DNS: Unknown host: '206.206.33.66.sbl.spamhaus.org'

SAT SEP 26 04:56:43 2009 DNS: Unknown host: '10.8.222.67.sbl.spamhaus.org'

SAT SEP 26 04:56:43 2009 DNS: Unknown host: '75.178.9.204.sbl.spamhaus.org'

SAT SEP 26 04:56:43 2009 DNS: Unknown host: '82.123.19.67.sbl.spamhaus.org'

SAT SEP 26 04:56:43 2009 DNS: Unknown host: '64.18.82.208.sbl.spamhaus.org'

SAT SEP 26 04:56:43 2009 DNS: Unknown host: '96.16.82.208.sbl.spamhaus.org'

SAT SEP 26 04:56:43 2009 DNS: Unknown host: '216.216.33.66.sbl.spamhaus.org'

SAT SEP 26 04:56:43 2009 DNS: Unknown host: '10.38.239.216.sbl.spamhaus.org'

SAT SEP 26 04:56:43 2009 DNS: Unknown host: '10.36.239.216.sbl.spamhaus.org'

SAT SEP 26 04:56:43 2009 DNS: Unknown host: '72.251.234.209.sbl.spamhaus.org'

SAT SEP 26 04:56:41 2009 DNS: Unknown host: '1.114.74.204.sbl.spamhaus.org'

SAT SEP 26 04:56:41 2009 DNS: Unknown host: '12.231.250.216.sbl.spamhaus.org'

SAT SEP 26 04:56:41 2009 DNS: Unknown host: '1.109.74.204.sbl.spamhaus.org'

SAT SEP 26 04:56:40 2009 DNS: Unknown host: '194.176.45.207.sbl.spamhaus.org'

SAT SEP 26 04:56:40 2009 DNS: Unknown host: '172.0.24.65.sbl.spamhaus.org'

SAT SEP 26 04:56:40 2009 DNS: Unknown host: '19.201.30.24.sbl.spamhaus.org'

SAT SEP 26 04:56:40 2009 DNS: Unknown host: '19.200.30.24.sbl.spamhaus.org'

SAT SEP 26 04:56:39 2009 DNS: Unknown host: '200.20.52.152.sbl.spamhaus.org'

SAT SEP 26 04:56:39 2009 DNS: Unknown host: '184.28.27.64.sbl.spamhaus.org'

SAT SEP 26 04:56:38 2009 DNS: Unknown host: '1.69.7.199.sbl.spamhaus.org'

SAT SEP 26 04:56:38 2009 DNS: Unknown host: '31.195.220.74.sbl.spamhaus.org'

SAT SEP 26 04:56:38 2009 DNS: Unknown host: '16.11.100.208.sbl.spamhaus.org'

SAT SEP 26 04:56:38 2009 DNS: Unknown host: '10.252.52.152.sbl.spamhaus.org'

SAT SEP 26 04:56:38 2009 DNS: Unknown host: '60.104.90.66.sbl.spamhaus.org'

SAT SEP 26 04:56:37 2009 DNS: Unknown host: '168.253.108.166.sbl.spamhaus.org'

SAT SEP 26 04:56:37 2009 DNS: Unknown host: '1.68.7.199.sbl.spamhaus.org'

SAT SEP 26 04:56:37 2009 DNS: Unknown host: '1.108.74.204.sbl.spamhaus.org'

SAT SEP 26 04:56:37 2009 DNS: Unknown host: '13.231.250.216.sbl.spamhaus.org'

SAT SEP 26 04:56:37 2009 DNS: Unknown host: '135.1.52.152.sbl.spamhaus.org'

SAT SEP 26 04:56:36 2009 DNS: Unknown host: '1.115.74.204.sbl.spamhaus.org'

SAT SEP 26 04:56:32 2009 DNS: Unknown host: '120.148.42.162.list.dnswl.org'

SAT SEP 26 04:56:32 2009 DNS: Unknown host: 'logonbasic.com.fulldom.rfc-ignorant.org'

SAT SEP 26 04:56:32 2009 DNS: Unknown host: '120.148.42.162.iadb.isipp.com'

SAT SEP 26 04:56:32 2009 DNS: Unknown host: '120.148.42.162.sa-trusted.bondedsender.org'

SAT SEP 26 04:56:32 2009 DNS: Unknown host: '120.148.42.162.sa-accredit.habeas.com'

SAT SEP 26 04:56:32 2009 DNS: Unknown host: 'logonbasic.com.bl.open-whois.org'

SAT SEP 26 04:56:31 2009 DNS: Unknown host: '120.148.42.162.dnsbl.sorbs.net'

SAT SEP 26 04:56:31 2009 DNS: Unknown host: '120.148.42.162.plus.bondedsender.org'

SAT SEP 26 04:56:31 2009 DNS: Unknown host: '9.227.25.98.bl.spamcop.net'

SAT SEP 26 04:56:31 2009 DNS: Unknown host: 'logonbasic.com.rhsbl.ahbl.org'

SAT SEP 26 04:56:31 2009 DNS: Unknown host: '120.148.42.162.combined.njabl.org'

SAT SEP 26 04:56:31 2009 DNS: Unknown host: '120.148.42.162.bl.spamcop.net'

SAT SEP 26 04:56:31 2009 DNS: Unknown host: '120.148.42.162.zen.spamhaus.org'

SAT SEP 26 04:56:31 2009 DNS: Unknown host: '9.227.25.98.combined.njabl.org'

SAT SEP 26 04:56:30 2009 DNS: Unknown host: 'lewrockwell.com.multi.surbl.org'

SAT SEP 26 04:56:30 2009 DNS: Unknown host: 'infowars.com.multi.surbl.org'

SAT SEP 26 04:56:30 2009 DNS: Unknown host: 'infowars.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:30 2009 DNS: Unknown host: 'lewrockwell.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:30 2009 DNS: Unknown host: '9.227.25.98.sa-other.bondedsender.org'

SAT SEP 26 04:56:30 2009 DNS: Unknown host: 'infowars.com.multi.uribl.com'

SAT SEP 26 04:56:30 2009 DNS: Unknown host: 'infowars.com.bl.open-whois.org'

SAT SEP 26 04:56:30 2009 DNS: Unknown host: 'lewrockwell.com.bl.open-whois.org'

SAT SEP 26 04:56:29 2009 DNS: Unknown host: 'usconstitution.net.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:29 2009 DNS: Unknown host: 'youtube.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:29 2009 DNS: Unknown host: 'youtube.com.multi.surbl.org'

SAT SEP 26 04:56:29 2009 DNS: Unknown host: 'lewrockwell.com.multi.uribl.com'

SAT SEP 26 04:56:29 2009 DNS: Unknown host: 'usconstitution.net.multi.surbl.org'

SAT SEP 26 04:56:29 2009 DNS: Unknown host: 'usconstitution.net.multi.uribl.com'

SAT SEP 26 04:56:29 2009 DNS: Unknown host: 'usconstitution.net.bl.open-whois.org'

SAT SEP 26 04:56:29 2009 DNS: Unknown host: 'youtube.com.bl.open-whois.org'

SAT SEP 26 04:56:28 2009 DNS: Unknown host: 'wnd.com.multi.surbl.org'

SAT SEP 26 04:56:28 2009 DNS: Unknown host: 'typepad.com.multi.surbl.org'

SAT SEP 26 04:56:28 2009 DNS: Unknown host: 'wnd.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:28 2009 DNS: Unknown host: 'typepad.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:28 2009 DNS: Unknown host: 'wnd.com.multi.uribl.com'

SAT SEP 26 04:56:28 2009 DNS: Unknown host: 'youtube.com.multi.uribl.com'

SAT SEP 26 04:56:28 2009 DNS: Unknown host: 'wnd.com.bl.open-whois.org'

SAT SEP 26 04:56:28 2009 DNS: Unknown host: 'typepad.com.bl.open-whois.org'

SAT SEP 26 04:56:27 2009 DNS: Unknown host: 'springerlink.com.multi.uribl.com'

SAT SEP 26 04:56:27 2009 DNS: Unknown host: 'typepad.com.multi.uribl.com'

SAT SEP 26 04:56:27 2009 DNS: Unknown host: 'springerlink.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:27 2009 DNS: Unknown host: 'phoenixnewtimes.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:27 2009 DNS: Unknown host: 'springerlink.com.multi.surbl.org'

SAT SEP 26 04:56:27 2009 DNS: Unknown host: 'phoenixnewtimes.com.multi.surbl.org'

SAT SEP 26 04:56:27 2009 DNS: Unknown host: 'springerlink.com.bl.open-whois.org'

SAT SEP 26 04:56:27 2009 DNS: Unknown host: 'phoenixnewtimes.com.bl.open-whois.org'

SAT SEP 26 04:56:26 2009 DNS: Unknown host: '24hourforums.com.multi.surbl.org'

SAT SEP 26 04:56:26 2009 DNS: Unknown host: 'visitpittsburgh.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:26 2009 DNS: Unknown host: '24hourforums.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:26 2009 DNS: Unknown host: 'visitpittsburgh.com.multi.surbl.org'

SAT SEP 26 04:56:26 2009 DNS: Unknown host: 'phoenixnewtimes.com.multi.uribl.com'

SAT SEP 26 04:56:26 2009 DNS: Unknown host: 'visitpittsburgh.com.multi.uribl.com'

SAT SEP 26 04:56:26 2009 DNS: Unknown host: 'visitpittsburgh.com.bl.open-whois.org'

SAT SEP 26 04:56:26 2009 DNS: Unknown host: '24hourforums.com.bl.open-whois.org'

SAT SEP 26 04:56:25 2009 DNS: Unknown host: 'lonestartimes.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:25 2009 DNS: Unknown host: 'constitution.org.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:25 2009 DNS: Unknown host: 'lonestartimes.com.multi.surbl.org'

SAT SEP 26 04:56:25 2009 DNS: Unknown host: '24hourforums.com.multi.uribl.com'

SAT SEP 26 04:56:25 2009 DNS: Unknown host: 'constitution.org.multi.surbl.org'

SAT SEP 26 04:56:25 2009 DNS: Unknown host: 'lonestartimes.com.multi.uribl.com'

SAT SEP 26 04:56:25 2009 DNS: Unknown host: 'lonestartimes.com.bl.open-whois.org'

SAT SEP 26 04:56:25 2009 DNS: Unknown host: 'constitution.org.bl.open-whois.org'

SAT SEP 26 04:56:24 2009 DNS: Unknown host: 'ktul.com.multi.surbl.org'

SAT SEP 26 04:56:24 2009 DNS: Unknown host: 'ktul.com.multi.uribl.com'

SAT SEP 26 04:56:24 2009 DNS: Unknown host: 'mcclatchydc.com.multi.surbl.org'

SAT SEP 26 04:56:24 2009 DNS: Unknown host: 'ktul.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:24 2009 DNS: Unknown host: 'mcclatchydc.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:24 2009 DNS: Unknown host: 'constitution.org.multi.uribl.com'

SAT SEP 26 04:56:24 2009 DNS: Unknown host: 'ktul.com.bl.open-whois.org'

SAT SEP 26 04:56:24 2009 DNS: Unknown host: 'mcclatchydc.com.bl.open-whois.org'

SAT SEP 26 04:56:23 2009 DNS: Unknown host: 'infowars.net.multi.surbl.org'

SAT SEP 26 04:56:23 2009 DNS: Unknown host: 'myfoxaustin.com.multi.surbl.org'

SAT SEP 26 04:56:23 2009 DNS: Unknown host: 'myfoxaustin.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:23 2009 DNS: Unknown host: 'infowars.net.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:23 2009 DNS: Unknown host: 'myfoxaustin.com.multi.uribl.com'

SAT SEP 26 04:56:23 2009 DNS: Unknown host: 'mcclatchydc.com.multi.uribl.com'

SAT SEP 26 04:56:23 2009 DNS: Unknown host: 'myfoxaustin.com.bl.open-whois.org'

SAT SEP 26 04:56:23 2009 DNS: Unknown host: 'infowars.net.bl.open-whois.org'

SAT SEP 26 04:56:22 2009 DNS: Unknown host: 'ning.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:22 2009 DNS: Unknown host: 'az-sta.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:22 2009 DNS: Unknown host: 'infowars.net.multi.uribl.com'

SAT SEP 26 04:56:22 2009 DNS: Unknown host: 'ning.com.multi.uribl.com'

SAT SEP 26 04:56:22 2009 DNS: Unknown host: 'ning.com.multi.surbl.org'

SAT SEP 26 04:56:22 2009 DNS: Unknown host: 'az-sta.com.multi.surbl.org'

SAT SEP 26 04:56:22 2009 DNS: Unknown host: 'ning.com.bl.open-whois.org'

SAT SEP 26 04:56:22 2009 DNS: Unknown host: 'az-sta.com.bl.open-whois.org'

SAT SEP 26 04:56:21 2009 DNS: Unknown host: 'www.co.travis.tx.us.multi.uribl.com'

SAT SEP 26 04:56:21 2009 DNS: Unknown host: 'www.co.travis.tx.us.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:21 2009 DNS: Unknown host: 'thenewamerican.com.dob.sibl.support-intelligence.net'

SAT SEP 26 04:56:21 2009 DNS: Unknown host: 'az-sta.com.multi.uribl.com'

SAT SEP 26 04:56:21 2009 DNS: Unknown host: 'thenewamerican.com.multi.surbl.org'

SAT SEP 26 04:56:21 2009 DNS: Unknown host: 'www.co.travis.tx.us.multi.surbl.org'

SAT SEP 26 04:56:21 2009 DNS: Unknown host: 'thenewamerican.com.multi.uribl.com'

SAT SEP 26 04:56:21 2009 DNS: Unknown host: 'www.co.travis.tx.us.bl.open-whois.org'

SAT SEP 26 04:56:21 2009 DNS: Unknown host: 'thenewamerican.com.bl.open-whois.org'

```

So the vonage box and my DSL modem do not want to play nice together (not an Ubuntu issue) but what are all these log entries?

eb

---

### Post by dearingj on 2009-09-26
Since you've got so few devices, probably the simplest solution would be to unplug one, leave it unplugged long enough to see whether the modem still crashes, and then plug it in (if it's not the culprit) and try another. Keep going until you've tried all 3 of your devices.

---

### Post by dearingj on 2009-09-26
It might be related to SpamAssassin. I've heard of SpamHaus.org before; they apparently do provide anti-spam protection of some kind.

---

### Post by Razmear on 2009-09-26
Yeah, spamhaus sounds familiar, but where did this one come from? 
SAT SEP 26 05:59:23 2009 DNS: Unknown host: 'blackfamilyonline.com.fulldom.rfc-ignorant.org' 

I'm guessing i'm not a hijacked machine, i think its just the vonage box competing with my dsl modem to be the DHCP host thats causing the disconnect problems. This not being a vonage forum I'll surpress my need to rant about all the little glitches so far from the 'reconditioned' box they sent me. 

Thanks for the help,
eb

---

