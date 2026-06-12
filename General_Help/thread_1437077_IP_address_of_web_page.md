---
title: "IP address of web page?"
date: 2010-03-23
forum: General Help
---

### Post by cpeachey on 2010-03-23
Using Firefox how can I find the IP address of a particular web page please?
Chris

---

### Post by era86 on 2010-03-23
Doing a google on "find the IP address of a particular web page"... go to the first result.  Shows how you can use ping to do it.

---

### Post by cpeachey on 2010-03-23
I did try ping with Terminal...
sudo ping [http://www.metoffice.gov.uk/weather/uk/ee/chelmsford_forecast_weather.html](http://www.metoffice.gov.uk/weather/uk/ee/chelmsford_forecast_weather.html)
but it did not work. I presume I did not type the right command?
Chris

---

### Post by linden940 on 2010-03-23
go to system > administration > network tools 

when that comes up you can click into lookup, whois or ping

if you click and use ping at the bottom there is a details..click on it and it will tell you the ip address there...lookup and whois will tell you the ip address as well as well as give you other information as well

all you have to type is the web address in any of those boxs and it will work...like google.com

---

### Post by -grubby on 2010-03-23
You can use this page: [http://www.selfseo.com/find_ip_address_of_a_website.php](http://www.selfseo.com/find_ip_address_of_a_website.php)

Edit: Why are you using sudo with ping?

---

### Post by cpeachey on 2010-03-23
Thanks all. I have sorted it now.
Chris

---

### Post by sublimation on 2010-03-23
> **cpeachey said:**
> I did try ping with Terminal...
sudo ping [http://www.metoffice.gov.uk/weather/uk/ee/chelmsford_forecast_weather.html](http://www.metoffice.gov.uk/weather/uk/ee/chelmsford_forecast_weather.html)
but it did not work. I presume I did not type the right command?
Chris

Actually, when you ping, you're checking for a server, not a specific webpage. So, if you want to ping a server, just remove the http:// (you're pinging, not using HyperText Transfer Protocol) and remove everything after the first / (those are folders on the server)

So:
```
you@host:~$ ping www.metoffice.gov.uk
PING a376.b.akamai.net (165.254.148.179) 56(84) bytes of data.
64 bytes from 165.254.148.179: icmp_seq=1 ttl=48 time=38.4 ms
64 bytes from 165.254.148.179: icmp_seq=2 ttl=48 time=40.0 ms

--- a376.b.akamai.net ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 5072ms
rtt min/avg/max/mdev = 38.442/39.255/40.069/0.837 ms
```
Yeah, a bit of long ping from across the ocean...

---

### Post by bodhi.zazen on 2010-03-23
There are also firefox extensions, such as show IP ...

---

### Post by pricetech on 2010-03-23
> **bodhi.zazen said:**
> There are also firefox extensions, such as show IP ...

Which is more in line with how the original question reads.  But outside of Firefox:

Ping might not work since some networks have taken to dropping ping packets.  nslookup is a better tool.

---

### Post by bodhi.zazen on 2010-03-23
There are also several online tools if you prefer.

google search "whois"

---

### Post by pbrane on 2010-03-23
> **pricetech said:**
> Which is more in line with how the original question reads.  But outside of Firefox:

Ping might not work since some networks have taken to dropping ping packets.  nslookup is a better tool.

ping should still work. It has to do a name lookup before it can ping the host. But ping won't "ping" a page. only the site.
```

ping www.metoffice.gov.uk
PING a376.b.akamai.net (65.199.63.128) 56(84) bytes of data.
64 bytes from 65.199.63.128: icmp_seq=1 ttl=51 time=56.5 ms
64 bytes from 65.199.63.128: icmp_seq=2 ttl=51 time=60.3 ms
^C64 bytes from 65.199.63.128: icmp_seq=3 ttl=51 time=93.9 ms

--- a376.b.akamai.net ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2355ms
rtt min/avg/max/mdev = 56.574/70.304/93.983/16.815 ms

```

---

### Post by hselvaggi on 2010-03-23
You should ping the server for example [http://server/some/page.html](http://server/some/page.html)

do something like ping server

Regards:
Harold.

---

### Post by sublimation on 2010-03-23
well, isn't this interesting:
> **pbrane said:**
> 
```
ping www.metoffice.gov.uk
PING a376.b.akamai.net (65.199.63.128) 56(84) bytes of data.
```


> **sublimation said:**
> 
```
ping www.metoffice.gov.uk
PING a376.b.akamai.net (165.254.148.179) 56(84) bytes of data.
```


---

### Post by pbrane on 2010-03-23
> **sublimation said:**
> well, isn't this interesting:

Probably mirrored servers in different geographical locations. I should have read that thread closer. You had the right idea early on.

---

### Post by Enigmapond on 2010-03-23
Install flagfox plugin. This will show you the country and also the IP.

[https://addons.mozilla.org/en-US/firefox/addon/5791](https://addons.mozilla.org/en-US/firefox/addon/5791)

---

