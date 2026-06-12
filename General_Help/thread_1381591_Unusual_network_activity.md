---
title: "Unusual network activity"
date: 2010-01-14
forum: General Help
---

### Post by t0p on 2010-01-14
I'm running Ubuntu Hardy. I ran *netstat -tcp* and saw lots of network activity that I don't recognise.  Lot's of "tor" stuff, and I don't use tor...

Anyway, check out this output.  Note this activity was happening *when I didn't have a web browser open* and the only network-related app that I knew was on was Dropbox:

```

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 10.173.186.40:55581     ip-62-143-234-93.:https ESTABLISHED 8412/tor        
tcp        0      0 10.173.186.40:42488     anonymizer2.blutm:https ESTABLISHED 8412/tor        
tcp        0      0 10.173.186.40:60971     kyra.desire.se:9001     ESTABLISHED 8412/tor        
tcp        0      0 10.173.186.40:48533     cyberphunk.eu:9001      ESTABLISHED 8412/tor        
tcp        0      0 10.173.186.40:36539     vpn.nerdsurf.de:19001   ESTABLISHED 8412/tor        
tcp        0      0 10.173.186.40:37997     5357422C.cable.cas:9001 ESTABLISHED 8412/tor        
tcp        0      0 10.173.186.40:34533     tor.tnode.com:https     ESTABLISHED 8412/tor        
tcp        0      0 10.173.186.40:38347     78.142.140.194:9001     ESTABLISHED 8412/tor        
tcp        0      0 10.173.186.40:37845     alpha.rueckgr.at:9001   ESTABLISHED 8412/tor        
tcp        0      0 10.173.186.40:33905     78.31.64.94:9001        ESTABLISHED 8412/tor        
tcp        0      0 10.173.186.40:59712     nothing-12.ams.lo:https ESTABLISHED 8412/tor        
tcp        0      0 10.173.186.40:44305     upcensors.net:9001      ESTABLISHED 8412/tor        
tcp        0      0 10.173.186.40:42163     cursa.CARNet.hr:9090    ESTABLISHED 8412/tor        
tcp        0      0 10.173.186.40:36701     83-65-91-108.work:https ESTABLISHED 8412/tor        
tcp        0      0 10.173.186.40:42295     208.43.202.44-stati:www ESTABLISHED 9894/dropbox    
tcp        0      0 10.173.186.40:55753     static.66.178.40.1:9001 ESTABLISHED 8412/tor 
```See all that tor stuff?  What on earth is causing that?

---

### Post by Ahadiel on 2010-01-15
From the looks of your netstat... it seems to be Tor traffic.
[http://en.wikipedia.org/wiki/Tor_(anonymity_network)](http://en.wikipedia.org/wiki/Tor_(anonymity_network))

---

### Post by t0p on 2010-01-15
> **Ahadiel said:**
> From the looks of your netstat... it seems to be Tor traffic.
[http://en.wikipedia.org/wiki/Tor_(anonymity_network)]("http://en.wikipedia.org/wiki/Tor_%28anonymity_network%29")

Yes I know it's tor traffic.  But I don't use tor.

I decided to end the tor process.  So I tried to end it through System Monitor.  But when I clicked to confirm ending the process... System Monitor crashed.

So I killed it with *sudo pkill tor*.  Now the tor traffic has stopped.  But I still don't know why it was running in the first place.  *I don't use tor*.  I did install it some time ago, but I haven't used it in ages.  So why was it running?

---

### Post by Ahadiel on 2010-01-15
> **t0p said:**
> Yes I know it's tor traffic.  But I don't use tor.

I decided to end the tor process.  So I tried to end it through System Monitor.  But when I clicked to confirm ending the process... System Monitor crashed.

So I killed it with *sudo pkill tor*.  Now the tor traffic has stopped.  But I still don't know why it was running in the first place.  *I don't use tor*.  I did install it some time ago, but I haven't used it in ages.  So why was it running?

Perhaps the tor daemon automatically starts (like most apt-installable daemons).

---

### Post by t0p on 2010-01-15
> **Ahadiel said:**
> Perhaps the tor daemon automatically starts (like most apt-installable daemons).

Perhaps.  But I've never noticed this happening before.

Anyway, I've removed tor now.  I don't want to use it, so I don't need it installed.  But I'm still puzzled.

---

