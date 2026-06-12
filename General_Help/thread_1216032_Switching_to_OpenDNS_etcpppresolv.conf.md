---
title: "Switching to OpenDNS: /etc/ppp/resolv.conf"
date: 2009-07-17
forum: General Help
---

### Post by mac9416 on 2009-07-17
Hi, ya'll!

    I've been trying to switch to OpenDNS, but I have had a terrible time. I followed the instructions on their website by editing my wireless broadband settings to use the OpenDNS servers. NetworkManager edited my /etc/resolv.conf to include the OpenDNS servers, but it still was not working. On a hunch, I looked at my /etc/ppp/resolv.conf. It was not configured with OpenDNS IP addresses. So I changed them and rebooted. When it booted back up the /etc/ppp/resolv.conf had been set back to the old IPs. I have repeated the same process several times with the same result.

   Basically, my goal is to prevent _something_ from changing my /etc/ppp/resolv.conf back each time I restart.

Thanks in advance for any help!

---

### Post by t4thfavor on 2009-07-17
Set static DNS inside your dialup connection (yes wireless broadband is dialup) I am familliar with doing this on a real 56k dialup, but it cannot be much different from what your doing.

Are you using GnomePPP? If so it should be easy.

---

### Post by darco on 2009-07-17
I dont know if this affects wireless connections but I know for my wired connection, I had to add "prepend domain-name-servers 208.67.222.222,208.67.220.220;" to /etc/dhcp3/dhclient.conf 

good luck
darco

---

### Post by t4thfavor on 2009-07-18
From what it looks like this is  a wireless ppp connection, like a gsm or cdma modem. It would be handled by the pppd, thats why stuff is getting overwritten.

---

### Post by mac9416 on 2009-07-18
> **t4thfavor said:**
> Set static DNS inside your dialup connection (yes wireless broadband is dialup) I am familliar with doing this on a real 56k dialup, but it cannot be much different from what your doing.

Are you using GnomePPP? If so it should be easy.

I have been right-clicking the NetworkManager Applet and clicking Edit Connections. Editing the settings for that connection, I see no way to set the IP to static. I installed GnomePPP, but there are so many settings to set up the connection I don't know where to start. The defaults don't work.

> I dont know if this affects wireless connections but I know for my wired connection, I had to add "prepend domain-name-servers 208.67.222.222,208.67.220.220;" to /etc/dhcp3/dhclient.conf

I did that, still no good. :-(

> From what it looks like this is a wireless ppp connection, like a gsm or cdma modem. It would be handled by the pppd, thats why stuff is getting overwritten.

It's a CDMA modem, though I'm not sure what that means.

Thanks for ya'll's help, but I'm still just about where I started.

---

### Post by t4thfavor on 2009-07-18
CDMA is cellular, who is your provider?

If you an get to the edit wondow that liiks like this, you can pick pppd(address only, and set the dns servers accordingly.

I have attached a screenshot to help show you what it looks like.

---

### Post by mac9416 on 2009-07-18
My provider is Verizon.

Here is what my settngs look like. (screenshot)

Like I say, NetworkManager has managed to edit my /etc/resolv.conf, but /etc/ppp/resolv.conf still has the old DNS's.

---

### Post by t4thfavor on 2009-07-18
Do a query for a domain like so"

```

dig adomain.com

```

look for the nameserver, and see what its giving you, mine looks like this becausse i have my own internal DNS proxy.

```

chance@netbook:~$ dig nbisolutions.net

; <<>> DiG 9.5.1-P2 <<>> nbisolutions.net
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 53677
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 4

;; QUESTION SECTION:
;nbisolutions.net.		IN	A

;; ANSWER SECTION:
nbisolutions.net.	3600	IN	A	64.119.50.10

;; AUTHORITY SECTION:
nbisolutions.net.	964	IN	NS	ns4.nameresolve.com.
nbisolutions.net.	964	IN	NS	ns3.nameresolve.com.
nbisolutions.net.	964	IN	NS	ns2.nameresolve.com.
nbisolutions.net.	964	IN	NS	ns1.nameresolve.com.

;; ADDITIONAL SECTION:
ns1.nameresolve.com.	82516	IN	A	64.94.117.197
ns2.nameresolve.com.	66131	IN	A	63.251.83.67
ns3.nameresolve.com.	5197	IN	A	66.150.161.150
ns4.nameresolve.com.	15966	IN	A	64.94.31.81

;; Query time: 53 msec
;; SERVER: 192.168.2.1#53(192.168.2.1)
;; WHEN: Sat Jul 18 13:57:37 2009
;; MSG SIZE  rcvd: 201


```

192.168.2.1 was the nameserver I used, see what your using.

---

### Post by mac9416 on 2009-07-18
Here's what I got:

```
mac9416@mac9416-laptop:~$ dig google.com

; <<>> DiG 9.5.1-P2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 43434
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 4, ADDITIONAL: 2

;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		32	IN	A	74.125.45.100
google.com.		32	IN	A	74.125.67.100
google.com.		32	IN	A	74.125.127.100

;; AUTHORITY SECTION:
google.com.		61237	IN	NS	ns3.google.com.
google.com.		61237	IN	NS	ns4.google.com.
google.com.		61237	IN	NS	ns2.google.com.
google.com.		61237	IN	NS	ns1.google.com.

;; ADDITIONAL SECTION:
ns1.google.com.		72639	IN	A	216.239.32.10
ns3.google.com.		86230	IN	A	216.239.36.10

;; Query time: 135 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sat Jul 18 15:57:38 2009
;; MSG SIZE  rcvd: 180

```

The server line looks like the OpenDNS IP. Weird, because when I go to welcome.opendns.com I get the "oops" page. Also, the craigslist.og test failed.

---

