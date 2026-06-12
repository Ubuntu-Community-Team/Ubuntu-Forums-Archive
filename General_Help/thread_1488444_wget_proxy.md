---
title: "wget proxy"
date: 2010-05-20
forum: General Help
---

### Post by vigge_sWe on 2010-05-20
When I try to use wget or install anything that uses wget to install (flash player plugin), it fails, as my IT admin blocks direct access to IPs.

I see wget takes the domain and resolves it's IP and then downloads (atleast thats how I get it?), and then I get "connection refused". Is it possible to force it use the domain and not the IP?

---

### Post by iponeverything on 2010-05-20
Set the global proxy setting trough 

System -> Preferences -> Network Proxy

to be the box that your organization is funneling the traffic through.

---

### Post by vigge_sWe on 2010-05-20
> **iponeverything said:**
> Set the global proxy setting trough 

System -> Preferences -> Network Proxy

to be the box that your organization is funneling the traffic through.

I already done that but the proxy blocks direct access to IPs, therefore I cannot use wget (I assume)

---

### Post by iponeverything on 2010-05-20
> **vigge_sWe said:**
> I already done that but the proxy blocks direct access to IPs, therefore I cannot use wget (I assume)

It's a proxy, it's job, as a proxy, is to proxy. 

The request goes to the proxy and the proxy fulfils the request for the client. - whether that client is wget, ie, firefox or something else.. it does not matter.

I don't really see where your getting hung up.  There is the system-wide setting that I mentioned my previous post that enables clients like wget to go through your organisations proxy instead of accessing sites directly. 

wget can made to use a proxy through an environment variable also:

[http://wiki.archlinux.org/index.php/Wget](http://wiki.archlinux.org/index.php/Wget)

---

### Post by vigge_sWe on 2010-05-20
> **iponeverything said:**
> It's a proxy, it's job, as a proxy, is to proxy. 

The request goes to the proxy and the proxy fulfils the request for the client. - whether that client is wget, ie, firefox or something else.. it does not matter.

I don't really see where your getting hung up.  There is the system-wide setting that I mentioned my previous post that enables clients like wget to go through your organisations proxy instead of accessing sites directly. 

wget can made to use a proxy through an environment variable also:

[http://wiki.archlinux.org/index.php/Wget](http://wiki.archlinux.org/index.php/Wget)

Example: 

> viggeswe@ROFFEL:~$ wget google.com
--2010-05-20 10:36:21--  [http://google.com/](http://google.com/)
Resolving google.com... 74.125.79.104, 74.125.79.147, 74.125.79.99
Connecting to google.com|74.125.79.104|:80... failed: Connection refused.
Connecting to google.com|74.125.79.147|:80... failed: Connection refused.
Connecting to google.com|74.125.79.99|:80... failed: Connection refused.


IPs are filtered out and blocked. I want it to connect to google.com, not 74.125.79.104, because that wont work. google is only an example. It happens everytime I use wget

env var is already set

> http_proxy="http://proxy1:8080/"


---

### Post by iponeverything on 2010-05-20
here is the skinny -- 

everything *including your web browser* turns the destination  into an IP address, before fulfiling the request.  

Nothing in IP goes directly to a site's name -it can't- that not how the IP protocol works.

just for fun grab tcpdump and see for yourself:

```
sudo apt-get install tcpdump

```

I should clarify the above for you, the proxy server is doing the name -> IP address conversion and not your host machine. Regardless, the communication is still IP to IP. 

start tcpdump

```
sudo tcpdump -n

```

use the browser to go to google. Then stop the tcpdump with ctrl-c.

The repeat the process using wget. Post your results.

---

### Post by vigge_sWe on 2010-05-20
> **iponeverything said:**
> here is the skinny -- 

everything *including your web browser* turns the destination  into an IP address, before fulfiling the request.  

Nothing in IP goes directly to a site's name -it can't- that not how the IP protocol works.

just for fun grab tcpdump and see for yourself:

```
sudo apt-get install tcpdump

```

start tcpdump

```
sudo tcpdump -n

```

use the browser to go to google. Then stop the tcpdump with ctrl-c.

The repeat the process using wget. Post your results.

There was no output, only this:

> viggeswe@ROFFEL:~$ sudo tcpdump -n
[sudo] password for viggeswe: 
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes

0 packets captured
0 packets received by filter
0 packets dropped by kernel


---

### Post by iponeverything on 2010-05-20
try replacing the "proxy1" with the actual ip address of the machine.

```
http_proxy="http://proxy1:8080/" 
```

---

### Post by iponeverything on 2010-05-20
> **vigge_sWe said:**
> There was no output, only this:

please use the -i option to tcpdump to instruct it to use the correct interface.

---

### Post by vigge_sWe on 2010-05-20
> **iponeverything said:**
> please use the -i option to tcpdump to instruct it to use the correct interface.

How do I get the name of the interface?

And I changed the proxy settings to the IP, no change.

Edit: got it.

Output from browser:

> viggeswe@ROFFEL:~$ sudo tcpdump -n -i wlan0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 96 bytes
11:21:20.571873 IP 10.232.100.66.50605 > 10.232.132.30.8080: Flags [P.], seq 2414204849:2414205779, ack 4229271500, win 204, options [nop,nop,TS val 381363 ecr 28700421], length 930
11:21:20.634941 IP 10.232.132.30.8080 > 10.232.100.66.50605: Flags [P.], seq 2897:3939, ack 930, win 65535, options [nop,nop,TS val 28701081 ecr 381363], length 1042
11:21:20.634998 IP 10.232.100.66.50605 > 10.232.132.30.8080: Flags [.], ack 1, win 204, options [nop,nop,TS val 381370 ecr 28700421,nop,nop,sack 1 {2897:3939}], length 0
11:21:20.635344 IP 10.232.132.30.8080 > 10.232.100.66.50605: Flags [.], seq 1:1449, ack 930, win 65535, options [nop,nop,TS val 28701081 ecr 381363], length 1448
11:21:20.635374 IP 10.232.100.66.50605 > 10.232.132.30.8080: Flags [.], ack 1449, win 227, options [nop,nop,TS val 381370 ecr 28701081,nop,nop,sack 1 {2897:3939}], length 0
11:21:20.635813 IP 10.232.132.30.8080 > 10.232.100.66.50605: Flags [.], seq 1449:2897, ack 930, win 65535, options [nop,nop,TS val 28701081 ecr 381363], length 1448
11:21:20.635840 IP 10.232.100.66.50605 > 10.232.132.30.8080: Flags [.], ack 3939, win 250, options [nop,nop,TS val 381370 ecr 28701081], length 0
11:21:20.636539 IP 10.232.132.30.8080 > 10.232.100.66.50605: Flags [P.], seq 5387:5708, ack 930, win 65535, options [nop,nop,TS val 28701081 ecr 381363], length 321
11:21:20.636564 IP 10.232.100.66.50605 > 10.232.132.30.8080: Flags [.], ack 3939, win 250, options [nop,nop,TS val 381370 ecr 28701081,nop,nop,sack 1 {5387:5708}], length 0
11:21:20.637078 IP 10.232.132.30.8080 > 10.232.100.66.50605: Flags [.], seq 3939:5387, ack 930, win 65535, options [nop,nop,TS val 28701081 ecr 381363], length 1448
11:21:20.637106 IP 10.232.100.66.50605 > 10.232.132.30.8080: Flags [.], ack 5708, win 272, options [nop,nop,TS val 381370 ecr 28701081], length 0
11:21:20.758961 IP 10.232.100.66.50550 > 10.232.132.30.8080: Flags [P.], seq 2535683393:2535684357, ack 405162778, win 394, options [nop,nop,TS val 381382 ecr 28700423], length 964
11:21:20.806458 IP 10.232.132.30.8080 > 10.232.100.66.50550: Flags [P.], seq 1:151, ack 964, win 64571, options [nop,nop,TS val 28701084 ecr 381382], length 150
11:21:20.806520 IP 10.232.100.66.50550 > 10.232.132.30.8080: Flags [.], ack 151, win 404, options [nop,nop,TS val 381387 ecr 28701084], length 0
11:21:20.813060 IP 10.232.100.66.50595 > 10.232.132.30.8080: Flags [P.], seq 1375820422:1375821549, ack 400481130, win 499, options [nop,nop,TS val 381387 ecr 28700424], length 1127
11:21:20.856259 IP 10.232.132.30.8080 > 10.232.100.66.50595: Flags [P.], seq 1:289, ack 1127, win 65535, options [nop,nop,TS val 28701084 ecr 381387], length 288
11:21:20.856296 IP 10.232.100.66.50595 > 10.232.132.30.8080: Flags [.], ack 289, win 497, options [nop,nop,TS val 381392 ecr 28701084], length 0



Output from using wget:

> viggeswe@ROFFEL:~$ sudo tcpdump -n -i wlan0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 96 bytes
11:22:26.282568 IP 10.232.100.66.40576 > 10.232.132.13.53: 20396+ AAAA? google.com. (28)
11:22:26.332800 IP 10.232.132.13.53 > 10.232.100.66.40576: 20396*- 0/1/0 (78)
11:22:26.333012 IP 10.232.100.66.48980 > 10.232.132.13.53: 3925+ AAAA? google.com.PORTALEN.INTRA. (43)
11:22:26.338574 IP 10.232.132.13.53 > 10.232.100.66.48980: 3925 NXDomain* 0/1/0 (112)
11:22:26.338687 IP 10.232.100.66.38218 > 10.232.132.13.53: 28479+ A? google.com. (28)
11:22:26.391257 IP 10.232.132.13.53 > 10.232.100.66.38218: 28479*- 3/0/0 A 74.125.79.99,[|domain]
11:22:26.391774 IP 10.232.100.66.37193 > 74.125.79.99.80: Flags [S], seq 2968630813, win 5840, options [mss 1460,sackOK,TS val 387945 ecr 0,nop,wscale 7], length 0
11:22:26.393975 IP 74.125.79.99.80 > 10.232.100.66.37193: Flags [R.], seq 0, ack 2968630814, win 5840, length 0
11:22:26.394380 IP 10.232.100.66.41327 > 74.125.79.104.80: Flags [S], seq 2979512045, win 5840, options [mss 1460,sackOK,TS val 387946 ecr 0,nop,wscale 7], length 0
11:22:26.396539 IP 74.125.79.104.80 > 10.232.100.66.41327: Flags [R.], seq 0, ack 2979512046, win 5840, length 0
11:22:26.396669 IP 10.232.100.66.46065 > 74.125.79.147.80: Flags [S], seq 2967974184, win 5840, options [mss 1460,sackOK,TS val 387946 ecr 0,nop,wscale 7], length 0
11:22:26.398856 IP 74.125.79.147.80 > 10.232.100.66.46065: Flags [R.], seq 0, ack 2967974185, win 5840, length 0
11:22:31.273534 ARP, Request who-has 10.232.100.1 tell 10.232.100.66, length 28
11:22:31.276526 ARP, Reply 10.232.100.1 is-at 00:17:95:27:3b:20, length 28



---

### Post by dcstar on 2010-05-20
[http://ubuntuforums.org/showthread.php?t=1488402](http://ubuntuforums.org/showthread.php?t=1488402)

---

### Post by iponeverything on 2010-05-20
```

export http_proxy="http://proxy1:8080/"

```

before running your wget in the same terminal.

---

### Post by vigge_sWe on 2010-05-20
> **dcstar said:**
> [http://ubuntuforums.org/showthread.php?t=1488402](http://ubuntuforums.org/showthread.php?t=1488402)

ahhh thanks that fixed it

---

### Post by iponeverything on 2010-05-20
> **vigge_sWe said:**
> ahhh thanks that fixed it

very good to hear.

---

### Post by amirmku on 2010-08-18
> **vigge_sWe said:**
> ahhh thanks that fixed it

Hi I am a newbie, I too have same problem as yours can you elaborate on how u solve this. It would be a great help

---

