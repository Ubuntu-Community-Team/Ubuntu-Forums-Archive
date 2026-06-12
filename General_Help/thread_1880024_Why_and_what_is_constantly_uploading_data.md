---
title: "Why and what is constantly uploading data?"
date: 2011-11-12
forum: General Help
---

### Post by ianc1 on 2011-11-12
Hi

I run Conky and it is always showing that I am uploading data at a rate of about 2 KiB presumably per second.  I don't remember this always being the case and it never seems to stop.

Should I be alarmed by this?  How do I go about working out what this is.  I tried netstat and but didn't understand the output.

Any help would be greatly appreciated.

Thanks

---

### Post by Habeouscorpus on 2011-11-13
If you have any program that remotely does anything with the internet, it could account for the 2 KiB. 2KiB isn't that much; it's about a page of typed plain text. 

Run netstat again, but run 

```
sudo netstat -tp 
``` and see who's doing the chatter.

---

### Post by alphacrucis2 on 2011-11-13
Another option is to run wireshark against your network interface(s) and capture everything. Install it via software centre or apt-get install if you prefer.

---

### Post by Uchiha_Kori on 2011-11-13
I, too, had a similar problem when I had uTorrent running back in my Windows 7 days. I don't know if it is cause for alarm or not, but I would also like to why it seems there is ALWAYS a transfer of data to the internet... :confused:

---

### Post by ianc1 on 2011-11-14
Thanks everyone

I've tried```
sudo netstat -tp
```and it shows nothing.  I've also never used torrents and checked to see that I haven't somehow inadvertently got one but I have no .torrent files.  I think all background services are off.

I've also installed wireshark but I'm a bit out of my depth here.  I reconfigured so that no root users could capture the interface and added myself to the wireshark group.  I can now see all wlan0 traffic.  Most to the rooter, and my web usage.  However I see some odd external ip addresses:

188.121.36.239 - which corresponds to Go Daddy a ducth ISP and hosting company.  Could a repository be using this?  If so why would I be receiving from this when not updating.

72.233.89.198 - which corresponds to LAYERED-TECH again a hosting company I think.  But not a lot of traffic.

I'm therefore still confused by conky's 2 kiB/s reading.  The network tool of system monitor confirms this value though.

I'm puzzled.  Any clues?  I'm tempted to do a fresh install, even though its a hassle to see if the problem goes away.

---

### Post by Silverflyer on 2011-11-14
```

```I did the Netstat-tp, because I was curious...

well, this is what I found.

```
jason@jason-MD2614U:~$ sudo netstat -tp
[sudo] password for jason: 
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 jason-MD2614U.loc:52339 a23-3-68-114.deploy:www TIME_WAIT   -               
tcp        0      0 jason-MD2614U.loc:52333 a23-3-68-114.deploy:www TIME_WAIT   -               
tcp        0      0 jason-MD2614U.loc:59389 216.104.220.207:www     TIME_WAIT   -               
tcp        0      0 jason-MD2614U.loc:42849 jabber-02-0:xmpp-client ESTABLISHED 11760/telepathy-gab
tcp        1      0 jason-MD2614U.loc:51582 a96-17-111-17.deplo:www CLOSE_WAIT  10495/gweather-appl
tcp        0      0 jason-MD2614U.loc:53415 pw-in-f125.:xmpp-client ESTABLISHED 11760/telepathy-gab
tcp        0      0 jason-MD2614U.loc:50212 fw.aarkay.com:www       ESTABLISHED 11239/firefox   
tcp        0      0 jason-MD2614U.loc:35542 209.67.103.115:www      ESTABLISHED 27809/npviewer.bin
tcp        0      0 jason-MD2614U.loc:35190 209.67.103.115:www      ESTABLISHED 27809/npviewer.bin
tcp        0      0 jason-MD2614U.loc:52335 a23-3-68-114.deploy:www TIME_WAIT   -               
tcp        0      0 jason-MD2614U.loc:35054 209.67.103.115:www      CLOSE_WAIT  27809/npviewer.bin
tcp        0      0 jason-MD2614U.loc:42814 sjc-not5.sjc.dropbo:www ESTABLISHED 10459/dropbox   
tcp        0      0 jason-MD2614U.loc:45745 iy-in-f16.1e100.n:imaps ESTABLISHED 10895/thunderbird-b
tcp        1      0 jason-MD2614U.loc:51581 a96-17-111-17.deplo:www CLOSE_WAIT  10495/gweather-appl
tcp        1      0 jason-MD2614U.loc:45769 a96-17-111-19.deplo:www CLOSE_WAIT  17494/gvfsd-http
tcp       38      0 jason-MD2614U.loc:44142 v-client-3a.sjc.d:https CLOSE_WAIT  10459/dropbox   
tcp        0      0 jason-MD2614U.loc:43251 iy-in-f16.1e100.n:imaps ESTABLISHED 10895/thunderbird-b
tcp        1      0 jason-MD2614U.loc:37978 8.27.255.254:www        CLOSE_WAIT  10495/gweather-appl
tcp        0      0 jason-MD2614U.loc:52336 a23-3-68-114.deploy:www TIME_WAIT   -               
tcp        0      0 jason-MD2614U.loc:43258 iy-in-f16.1e100.n:imaps ESTABLISHED 10895/thunderbird-b
tcp        0      0 jason-MD2614U.loc:50211 fw.aarkay.com:www       TIME_WAIT   -               
tcp        0      0 jason-MD2614U.loc:43257 iy-in-f16.1e100.n:imaps ESTABLISHED 10895/thunderbird-b

```

the one that has me most worried is Aarkay.com  I have no idea what it is, other than a server in Nassau Bahamas according to this [http://www.ip-adress.com/whois/aarkay.com](http://www.ip-adress.com/whois/aarkay.com)


this is the entry > tcp        0      0 jason-MD2614U.loc:50211 fw.aarkay.com:www       TIME_WAIT   -  

---

### Post by alphacrucis2 on 2011-11-14
> **ianc1 said:**
> Thanks everyone

I've tried```
sudo netstat -tp
```and it shows nothing.  I've also never used torrents and checked to see that I haven't somehow inadvertently got one but I have no .torrent files.  I think all background services are off.

I've also installed wireshark but I'm a bit out of my depth here.  I reconfigured so that no root users could capture the interface and added myself to the wireshark group.  I can now see all wlan0 traffic.  Most to the rooter, and my web usage.  However I see some odd external ip addresses:

188.121.36.239 - which corresponds to Go Daddy a ducth ISP and hosting company.  Could a repository be using this?  If so why would I be receiving from this when not updating.

72.233.89.198 - which corresponds to LAYERED-TECH again a hosting company I think.  But not a lot of traffic.

I'm therefore still confused by conky's 2 kiB/s reading.  The network tool of system monitor confirms this value though.

I'm puzzled.  Any clues?  I'm tempted to do a fresh install, even though its a hassle to see if the problem goes away.


conky can be configured to look up things like weather forecasts. I don't know if you are using it to do that though. The go daddy look up could be checking a certificate revocation list but I would only expect that sort of thing to occur when you open a https connection.

---

