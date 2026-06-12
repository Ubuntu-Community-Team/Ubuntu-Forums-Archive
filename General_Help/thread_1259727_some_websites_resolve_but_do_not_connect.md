---
title: "some websites resolve but do not connect"
date: 2009-09-06
forum: General Help
---

### Post by mnoyes on 2009-09-06
Upgraded to Ubuntu Jaunty, worked fine for several weeks, last week found that I could not access certain websites ([www.nytimes.com](www.nytimes.com), [www.ila1588.org](www.ila1588.org)) on either wired or wireless connection. 

Using Firefox 3.0.13 OpenDNS. Have been searching forums for days trying to find solutions (checked cables, rebooted router, disabled IPV6, set MTU to 1500, upgraded to firefox 3.5 then back down again... but none have worked so far. Help.

Also tried Wicd network manager. Still no go.

Have also had trouble with skype audio (lag) and with youtube video on fullscreen (lags). I know these are common problems, but the many solutions I have tried have not worked -- is there a connection here?:confused::confused:

---

### Post by mnoyes on 2009-09-08
Now it's a serious problem. I can't open the site that hosts my websites. This problem seems not to be Ubuntu-specific. It happens on windows xp, too, and can't be flash since different versions are being used. I really need help on this. If it is my router, any ideas how I begin to solve the problem? :confused:

---

### Post by credobyte on 2009-09-08
[LIST=1]
[*]Have you tried to contact your ISP ?
[*]Have you tried to reset ( settings to default ) your rooter ?
[/LIST]
As per what you say, can you show us an example of host, nslookup, dig and ping ?

---

### Post by mnoyes on 2009-09-08
> **credobyte said:**
> [LIST=1]
[*]Have you tried to contact your ISP ?
[*]Have you tried to reset ( settings to default ) your rooter ?
[/LIST]
As per what you say, can you show us an example of host, nslookup, dig and ping ?

First, thank you very much for your help. I have not yet tried to contact my ISP; there is a bit of a language barrier (I live in Japan) on top of a bit of a tech barrier (I'm not very technically adept). 

I have not tried to reset my router, hesitant to try this option.

Here is the info you asked about:

host nytimes.com
nytimes.com has address 199.239.136.200
nytimes.com mail is handled by 400 NYTIMES.COM.S7B2.PSMTP.com.
nytimes.com mail is handled by 100 NYTIMES.COM.S7A1.PSMTP.com.
nytimes.com mail is handled by 200 NYTIMES.COM.S7A2.PSMTP.com.
nytimes.com mail is handled by 300 NYTIMES.COM.S7B1.PSMTP.com.


nslookup
> [www.nytimes.com](www.nytimes.com)
Server:		208.67.222.222
Address:	208.67.222.222#53

Non-authoritative answer:
Name:	[www.nytimes.com](www.nytimes.com)
Address: 199.239.136.200


dig [www.nytimes.com](www.nytimes.com)

; <<>> DiG 9.5.1-P2 <<>> [www.nytimes.com](www.nytimes.com)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 22645
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.nytimes.com](www.nytimes.com).		IN	A

;; ANSWER SECTION:
[www.nytimes.com](www.nytimes.com).	87	IN	A	199.239.136.200

;; Query time: 105 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Wed Sep  9 01:03:50 2009
;; MSG SIZE  rcvd: 49


ping nytimes.com
PING nytimes.com (199.239.136.200) 56(84) bytes of data.
From 128.241.244.54 icmp_seq=11 Packet filtered
From 128.241.244.54 icmp_seq=20 Packet filtered
From 128.241.244.54 icmp_seq=25 Packet filtered
From 128.241.244.54 icmp_seq=29 Packet filtered
From 128.241.244.54 icmp_seq=40 Packet filtered
From 128.241.244.54 icmp_seq=46 Packet filtered
From 128.241.244.54 icmp_seq=51 Packet filtered
From 128.241.244.54 icmp_seq=81 Packet filtered

--- nytimes.com ping statistics ---
463 packets transmitted, 0 received, +54 errors, 100% packet loss, time 698141ms

---

### Post by mnoyes on 2009-09-08
On another site that I can't access:confused::

host ila1588.org
ila1588.org has address 74.50.28.205
ila1588.org mail is handled by 0 ila1588.org.
mnoyes@dell-desktop:~$ ping ila1588.org

nslookup [www.ila1588.org](www.ila1588.org)
Server:		208.67.220.220
Address:	208.67.220.220#53

Non-authoritative answer:
[www.ila1588.org](www.ila1588.org)	canonical name = ila1588.org.
Name:	ila1588.org
Address: 74.50.28.205


dig ila1588.org

; <<>> DiG 9.5.1-P2 <<>> ila1588.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 65053
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ila1588.org.			IN	A

;; ANSWER SECTION:
ila1588.org.		14220	IN	A	74.50.28.205

;; Query time: 106 msec
;; SERVER: 208.67.220.220#53(208.67.220.220)
;; WHEN: Wed Sep  9 12:07:10 2009
;; MSG SIZE  rcvd: 45


PING ila1588.org (74.50.28.205) 56(84) bytes of data.
^C
--- ila1588.org ping statistics ---
215 packets transmitted, 0 received, 100% packet loss, time 215457ms

---

### Post by credobyte on 2009-09-09
Open Firefox and open 199.239.136.200 - does it still show a blank ( not found ) page ?
The problem is that you can send requests, but doesn't receive an answer. Before pulling your hair out and trying to solve this, I would contact your ISP and ask them about this. It's not normal when you can't connect to these websites not only from Ubuntu, but other OS's as well.

---

### Post by mnoyes on 2009-09-09
Thanks credobyte. I will follow your advice.

Turns out that if I install Tor, I can access the sites, but they are very, very slow (not a criticism of tor, which seems like a virtuous project) and it makes it harder to access other sites.

I will post the solution from the ISP, if there is one...

Thanks for your help.

---

### Post by mnoyes on 2009-09-12
Checked with my ISP. They say that all is fine on their end but that nytimes.com and other sites are filtering ip addresses that start with 180. They (my ISP -- OCN) say that they have asked nytimes to stop filtering the IPs starting with 180 but have not had any luck. 

Tonight, another site that I maintain started having dns problems. I will try to figure it out, but this is big trouble.

Anyone have any idea how I can fix this? Why would it suddenly change -- had been working for months?:confused:

---

### Post by P4man on 2009-09-12
Not sure, but it sounds like the IP range of your provider was blacklisted. perhaps for good reason, perhaps accidentally, but there isn't much you can do about it. Either use something like Tor to contact sites with a different IP (but thats usually unacceptably slow), use a web proxy like:

[http://www.hidemyass.com/proxy/](http://www.hidemyass.com/proxy/)

Or switch providers.

---

### Post by mnoyes on 2009-09-12
Thanks. Not great options, but so it goes. I will try pressuring the ISP and then look for a new one -- this can't be good for them. The Ubuntu Forums have been, as usual, very helpful even if the news isn't good.

---

### Post by mnoyes on 2009-09-14
It turns out that my ISP -- OCN.ne.jp -- was allocated IP addresses starting with 180 and that because that address was until recently considered a [Bogon]("http://en.wikipedia.org/wiki/Bogon_filtering") many servers still block access from those IPs.

Solution: reset the IP address by rebooting the router, then check the IP address using [whatismyip.com]("http://whatismyip.com/"). Worked fine. This is an end of life problem for IPV4, it seems.

Thanks to ubuntu forum participants for helping me troubleshoot this.:)

---

