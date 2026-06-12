---
title: "Internet Stalls out?"
date: 2010-01-20
forum: General Help
---

### Post by Tourdog on 2010-01-20
I'm posting this problem here because of the ability of  knowledgeable gurus that are here!

The following problem is variable and intermittent.  It is manifest using Ubuntu or XP or Win7.   I use both the "Terminal" and "TraceRoute" to initiate and track Ping.  

Our ISP serves us via Micro-Wave at 2.435 ghertz.  It provides on average between 2 and 6 mbit download and maybe just shy of 1 mbit upload.

Our ability to move about various Web sites is very good.  Considering what cache provides or not...... but, at times.... all we get is an immediate:

"URL not found,  or Unable to Connect, and eventually Timed Out."  The results are a virtual slowdown to no ability to operate at all.  It happens any time of the day or night.
Speedtest.net or Speakeasy when we are "up" reports the speeds I've indicated above.

Ping Test will nearly always indicate a larger ms 1st packet and in nearly every test with a hundred packets sent 1 will be huge............   perhaps 5-600 ms where the rest are 20 ms.   These figures are true when I am pinging beyond my router ie using various IP addresses.

Is my router at fault?   What is happening?   Do all or most of you have similar ?  :(

---

### Post by Grenage on 2010-01-20
My first suspicion would be occasional interference (wireless connection, after all), but it's not impossible that the router is to blame.

---

### Post by Kevbert on 2010-01-20
What dou get with the terminal command
```
iwconfig
```
when connected. It may be interference as the previous poster suggested and show up as poor signal quality.

---

### Post by Tourdog on 2010-01-20
Grenage,
Kevbert,

Terminal:  iwconfig  

tourdog@PJK3:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"AutumnWx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:98:40:9C   
          Bit Rate=54 Mb/s   Tx-Power=6 dBm   
          Retry  long limit:7     RTS thr:0ff    Fragment thr:0ff
          Power Management:on
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tourdog@PJK3:~$ 

What do you think?

---

### Post by Kevbert on 2010-01-20
Signal Quality seems pretty good. Do you have a cordless phone nearby ? (they may work at 2.4GHz). Are you capped on what speed or amount downloaded every month (Is your SP throttling your internet) ?

---

### Post by Tourdog on 2010-01-20
Kevbert
No 2.4 ghertz except a Micro-wave oven but not in use.    You see the noise threshold -50 on the router is fairly quiet.   We both agree.  ISP only throttles the speed based on what you pay per month.............  no capping of quantity.

I have one computer (win7) cat 5 through the router on a Lan and the 3 others are wlan on channel 11  (2.462)  which is 27 mhz higher than the WAN (Motorola) uptop our tower (50').    Channel separation of 22 mhz is or should be adequate if the slope of the router's (Netgear) i.f. is adequately steep.  Cat 5 ethernet cable connects the wlan router to the Wan transceiver uptop the tower.  In Illinois this is a very common setup for broadband in low population areas.  

Sure is hard to find out why within moments of checking our speeds (7 mbit/sec) we can't get any internet but a few minutes  (or and hour) its like near instant access.

Sure appreciate your getting back!    Thank you!

---

### Post by arvevans on 2010-01-20
Seems there may be one more possible problem that has not been discussed.  You may get intermittent "bad URL" or "Site Not Found" messages if access to your DNS server is intermittent or has high packet loss.  A quick ping of the DNS primary and secondary would tell how reliable your access to DNS translations might be.

If it is found that your DNS server access is not reliable, you might want to try Google's relatively new DNS server at 8.8.8.8 with their 8.8.4.4 DNS as your secondary.  
_._

---

### Post by Grenage on 2010-01-20
I did ponder that, but it wouldn't explain the fact that a constant ping would suddenly jump up to 600ms or so.  Once an address has been resolved, it's cached and doesn't need to be looked up until the cached record expires.

Money is on external interference (not necessarily at the consumer end).

---

### Post by arvevans on 2010-01-20
OK.  Time for systematic troubleshooting. 
[LIST=1]
[*]Do a traceroute to some place that you may be having trouble reaching reliably.  Write down or save the hop addresses.
[*]Then, starting with the node closest to you, do a fairly long ping to see if there are any irregularities (long ping delay, or packet loss).
[*]If you don't see any problem, move your ping target out to the next node on your traceroute list, and re-do the ping test.
[*]Once you find the first node that gives you errors, that will point to the problem source.
[/LIST]

This may help to isolate the link that is causing the problem.  Unfortunately, you probably cannot do anything about it if it is out in the public network somewhere.

This is further complicated by the fact that network backbone routers do not send every packet via the same path.  It is possible that some network backbone link is bad, but a parallel link is good, thus giving you an intermittent problem.
_._

---

### Post by t0p on 2010-01-20
Have you asked other customers of the ISP if they get similar problems?  You may be wasting your time trying to track down the problem if it's down to the ISP.

Don't bother talking to the ISP's tech support - at least, not straight away.  They'll probably claim it's nothing to do with them.  Ask other customers.

---

### Post by Tourdog on 2010-01-20
Grenage,
Kevbert,
Arevans,
TOp,

Great!  You've given me some work to do and I DO appreciate it!  I was first on 900 mhz with this ISP and then moved to the 2.4 ghz with the promise of "thru-put" advantages!   And, of course more $$$ per month.  The frustration is huge when all of a sudden the dreaded "URL NOT FOUND" flies up and then one does not know if it is a temporary stall in seconds, or ......... minutes, .............  or an hour for that destination server.  The stunner is that singular  10 to 15X (longer than mean) ms packet on a multi-hop ping.   Some ISP's are notorious for overload but this is recorded as an"enroute" stumble.
I am working on it...................   thank you Gurus  !!!

I don't know anyone on this same site/ node.

---

