---
title: "some sites won't open"
date: 2010-04-07
forum: General Help
---

### Post by spandey on 2010-04-07
[SIZE=2]Hi,[/SIZE]
[SIZE=2]I am newbie to Linux. While surfing in Firefox, some websites won't open. But they open perfectly in Windows. How to find out what's the problem.[/SIZE]

---

### Post by kellemes on 2010-04-07
> **spandey said:**
> [SIZE=2]Hi,[/SIZE]
[SIZE=2]I am newbie to Linux. While surfing in Firefox, some websites won't open. But they open perfectly in Windows. How to find out what's the problem.[/SIZE]

What sites?

---

### Post by wojox on 2010-04-07
Try the troubleshooting: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by nischalinn on 2010-04-07
Try to open the site via *_terminal:_*

**firefox [http://sitename](http://sitename)**
And see what happens and post it back.

---

### Post by spandey on 2010-04-08
Hi,
Trying to open via Terminal 
firefox [http://www.indianrail.gov.in](http://www.indianrail.gov.in)

Firefox just says waiting for site [www.indianrail.gov.in]("http://www.indianrail.gov.in") ......

Most of the government of india websites same problem..

Expressbuzz.com will open but none of the news link will display any text...

---

### Post by nischalinn on 2010-04-08
Hey, I opened the site [www.indian........com](www.indian........com) from firefox and it opened. I think the problem might be due to heavy traffic of the website.

---

### Post by spandey on 2010-06-04
Still the same problem not able to open [www.indianrail.gov.in](www.indianrail.gov.in) with Lucid also. Any help how to fix this?

---

### Post by lisati on 2010-06-04
Not sure what the solution is.

A quick informal test at my end: [Expressbuzz.com]("http://expressbuzz.com/edition/default.aspx") wanted to open a popup (but my copy of Firefox didn't open it), the [Indiarail]("http://www.indianrail.gov.in/") site opened fine.

---

### Post by ryan858 on 2010-06-04
Maybe a DNS issue? All I can think of is try 8.8.8.8 (Google's free DNS) as your DNS server and see if it works better... To change DNS server, add this line to /etc/resolv.conf:
**nameserver 8.8.8.8**
and comment out the old nameserver.

Or you can use *System -> Preferences -> Network Connections* and set your connection to manual, set your info (IP, Gateway, etc) and set the DNS to 8.8.8.8. I'm pretty sure you have to set it to manual to use a custom DNS, unless you use resolv.conf, but even then it will be reset as soon as it auto-connects to the internet... Come to think of it, I don't know if it will read resolv.conf without restarting the connection...

---

### Post by arjunak01 on 2010-06-04
indianrail doesnt work in firefox and chromium. it is not a dns issue as i am using opendns and i can ping the site.but it works in opera

---

### Post by lisati on 2010-06-04
> **arjunak01 said:**
> indianrail doesnt work in firefox 

I'm wondering if it's a problem with FF settings or your cache. Displays fine on my copy of Firefox.

---

### Post by Stolea on 2010-06-04
I run Lucid with Firefox, Chromium and Opera. No problems opening the site.
Some ISPs (like here in Australia) are running black list filters. There is (however remote) the possibility that this site is for some strange reason on such a blacklist.
Welcome to the brave new world of government censorship.

---

### Post by lisati on 2010-06-04
I've done a bit of gazing into my crystal ball (actually my web site's log and a few other places): if you have trouble accessing a web site (mine included) it is possible that you are being blocked. 

Have a look here: [http://www.blacklistalert.org/](http://www.blacklistalert.org/)
(Note: the Blacklist Alert site is run by someone else. I am not responsible for the information it provides.)

---

### Post by Stolea on 2010-06-04
Hi Lisati,
I didn't know that your lot is as paranoid as our government :)

---

### Post by lisati on 2010-06-04
> **Stolea said:**
> Hi Lisati,
I didn't know that your lot is as paranoid as our government :)

Who's been snooping at my web site then? :)

I have some DNSBL-based blocking on my web site to help keep the spambots away. Unfortunately it sometimes blocks out innocent people. (Someone else who has looked at this thread was blocked.)

---

### Post by arjunak01 on 2010-06-04
> **lisati said:**
> Someone else who has looked at this thread was blocked
that would be me
:razz:

---

### Post by spandey on 2010-06-04
arjuna: 
[www.Indianrail.gov.in](www.Indianrail.gov.in) does work in OPERA as well. 

lisati:
//I'm wondering if it's a problem with FF settings or your cache. Displays  fine on my copy of Firefox.//  	

What settings in Firefox effect a website access?

---

### Post by dino99 on 2010-06-04
have you installed some plugins with firefox, like noscript or adblock, or have some blacklist into /etc/hosts or use a firewall or ipblock

---

### Post by spandey on 2010-06-05
No ad on like ad block etc. The etc/host has nothing. I have enabled GUFW firewall. The default option, incoming is denied.

---

### Post by Barafu Albino Cheetah on 2010-06-05
I wonder, this whole thread was never visited by any system administrator? 

The FIRST thing to do in case of any network problems is to PING. Because it divides the field of potential problem on two. 
```
ping www.thatidiansite.yo
```
What does it show? What percentage is packet loss? 

If it is more than 30% firefox can be opening site for ethernity.

---

### Post by sanderd17 on 2010-06-05
> **arjunak01 said:**
> that would be me
:razz:

I'm blocked to, when I go to [http://www.blacklistalert.org/](http://www.blacklistalert.org/) , I get the warning

> 
WARNING: No matching A-Record exists for: MY_IP_ADRESS
DNS is INCONSISTENT.
Please request your Admin or Provider to fix this.


inconsistent DNS? whats that?

---

### Post by dino99 on 2010-06-05
add into /etc/hosts:

nameserver 8.8.8.8  ## google

---

### Post by spandey on 2010-06-06
Ping to site [www.indianrail.gov.in](www.indianrail.gov.in) is filtered.

From 121.240.108.130.static-delhi.vsnl.net.in (121.240.108.130) icmp_seq=1 Packet filtered

All packets are filtered...

---

### Post by muffpants on 2010-08-19
[SIZE=2]Have you tried turning off tcp_window_scaling?

```
sudo echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```If this does cure the problem then put the command into /etc/rc.local (minus the 'sudo').

This is a problem with some routers not implementing the tcp standard properly rather than a problem with the websites or your networking stack.

Some background here:
[/SIZE][http://en.wikipedia.org/wiki/TCP_window_scale_option](http://en.wikipedia.org/wiki/TCP_window_scale_option)
[http://lwn.net/Articles/92727/](http://lwn.net/Articles/92727/)

---

