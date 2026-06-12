---
title: "Can't View Some website"
date: 2009-08-10
forum: General Help
---

### Post by mthalis on 2009-08-10
I have no proxy and I'm administrator of my network, I can't visit some website but same network other machine can visit that web site. What is the problem? Web site [http://www.topjobs.lk/](http://www.topjobs.lk/) 

Please help me..

---

### Post by philcamlin on 2009-08-10
what errors areyou getting can i see a screenshot

---

### Post by mthalis on 2009-08-10
I attached error screen shot with this thread

---

### Post by cariboo on 2009-08-10
You may be having a dns problem, can you ping google?

```
ping www.google.com
```

IF that doesn't work trying pinging by ip address:

```
ping 74.125.53.103
```

If you can ping by number and not by name, then you have a dns problem.

---

### Post by mthalis on 2009-08-10
Yes, I can ping google, but I can't ping [www.topjobs.lk](www.topjobs.lk), problem is other machine can also can't ping but it can vist that website.

---

### Post by joriad on 2009-08-10
Check your router configuration to make sure your mac address isn't being blocked. Also try to restart your computer modem and router, I have found sometimes that routers and modems just become stupid for no reason what so ever.

---

### Post by mthalis on 2009-08-10
I have two machine both Ubuntu, I gave network connection using switch, my one machine can visit that website other machine can't why, both machine can't ping that website also.

---

### Post by joriad on 2009-08-10
> **mthalis said:**
> I have two machine both Ubuntu, I gave network connection using switch, my one machine can visit that website other machine can't why, both machine can't ping that website also.

So are you trying to split the connection? I don't think that is possible that way.

---

### Post by mthalis on 2009-08-10
No, I gave seperate connection both of them(seperate ip).

---

### Post by roharme on 2009-08-10
change your DNS.
 
218.248.255.145
61.1.96.69

---

### Post by joriad on 2009-08-10
> **mthalis said:**
> No, I gave seperate connection both of them(seperate ip).

Ok, I guess i'm confused. Let me get this straight. 

You have one internet connection. 
You are using a switch to split the internet connection. 
You have no router.
Is this correct so far.

---

### Post by mthalis on 2009-08-10
No, I have router. Switch use for give local address(192.168.101.0)

Like roharme said I changed DNS 218.248.255.145,61.1.96.69 then work but can't ping using name, My default DNS 203.115.0.1,203.115.0.18

Problem is same network one machine can go but other can't.WHY

---

### Post by joriad on 2009-08-11
> **mthalis said:**
> No, I have router. Switch use for give local address(192.168.101.0)

Like roharme said I changed DNS 218.248.255.145,61.1.96.69 then work but can't ping using name, My default DNS 203.115.0.1,203.115.0.18

Problem is same network one machine can go but other can't.WHY

So you have one computer @192.168.101.0 and the other @192.168.101.1?
If that is the case you may have a problem with your internet provider I found this on a search that maybe of help. 

[HTML]http://answers.yahoo.com/question/index?qid=20070703114705AAdCR0G[/HTML]

---

### Post by mthalis on 2009-08-11
I don't know what happen in my machine now I can visit that website. Please help me to find out problem
What I did  
First
**roharme** said I changed DNS 218.248.255.145,61.1.96.69 than can go 

Next
Change **roharme** DNS to my original 203.115.0.1,203.115.0.18 then I can go

After reboot machine 
I can go that website

But couldn't ping that website using IP or name ?

But important point is now I visit that website using my old network configuration

I confused. Please help

---

### Post by joriad on 2009-08-11
I don't know all that technical details but sometimes a restart is necessary in order for all the settings to be activated. Everytime I had internet problems where I couldn't connect I called the provider and the first thing they did was to have me restart everything. Thats why I told you to restart everything first.

---

### Post by mthalis on 2009-08-11
You correct, but problem is I tried more than one week(normally shut-down machine) to visit that website. 

Still I confused.

---

### Post by joriad on 2009-08-11
Maybe there was something wrong with original dns to prevent it form connecting. And when you changed it and then changed it back again it could have corrected the problem. To be truthful, I think it was those computer gremlins, they have screwed with me a whole bunch of times.

---

### Post by mthalis on 2009-08-11
Please explain one this why I can't ping using Name or IP

If I tiped nslookup 
> 
ites@ites-desktop:~$ nslookup 220.247.224.87
Server:		203.115.0.1
Address:	203.115.0.1#53

87.224.247.220.in-addr.arpa	name = [www.topjobs.lk](www.topjobs.lk).


> 
ites@ites-desktop:~$ nslookup [www.topjobs.lk](www.topjobs.lk)
Server:		203.115.0.1
Address:	203.115.0.1#53

Non-authoritative answer:
Name:	[www.topjobs.lk](www.topjobs.lk)
Address: 220.247.224.87



[B]
WHY ?[/B]

---

### Post by QIII on 2009-08-11
A fellow poster, lovinglinux, has put together a great tutorial on optimizing Firefox.  Some of his suggestions my help.  Look specifically for disabling ipv6 in FF.

There is also the option of using OpenDNS in your network settings to get faster DNS resolution before you time out.

The tutorial can be found here:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

You can find out about OpenDNS here:

[http://www.opendns.com](http://www.opendns.com)

I was able to open the website.

By the way:  Which version of Ubuntu are you using and which version of FF?

---

### Post by joriad on 2009-08-11
> **mthalis said:**
> Please explain one this why I can't ping using Name or IP

If I tiped nslookup 




[B]
WHY ?[/B]

you may find the answer here
[HTML]http://www.cisco.com/en/US/products/sw/iosswrel/ps1831/products_tech_note09186a00800a6057.shtml#why_cant_i_ping[/HTML]

---

### Post by roharme on 2009-08-11
One small note.
 
Even i had such a setup in my home. But in windows. 
 
Gateway IP is 192.168.1.1(Router)
 
1. One system must be connected to the Internet .I did this via USB which is connected to my Modem.
 
The Configuration is 
Local IP **192.168.1.2**
Internet IP **59.12.23.44**(Say!!)
DNS **218.248.255.145 | 61.1.96.69**
 
2.The other system is connected to the one which is connected to the internet through LAN(RJ 45 cable)
 
The Configuration is 
Local IP **192.168.1.3**
**No DNS**
 
 
This set up worked perfectly for me.

---

### Post by mthalis on 2009-08-11
I'm using Ubuntu 9.04 and Firefox 3.0.13

---

### Post by sahan007 on 2010-03-21
I get a similar error when I access [http://www.lankatopjobs.org](http://www.lankatopjobs.org)
cant ping by number also

---

### Post by 98cwitr on 2010-03-21
^^^[http://220.247.224.87/](http://220.247.224.87/) = [http://www.lankatopjobs.org/](http://www.lankatopjobs.org/)

To OP,


[http://220.247.224.87/](http://220.247.224.87/)

^^^ip to the site. Try that, if it works you've got a DNS issue.

> **mthalis said:**
> Please explain one this why I can't ping using Name or IP

If I tiped nslookup 

[B]
WHY ?[/B]

I assume you tried it though, can you post a traceroute?


> **sahan007 said:**
> I get a similar error when I access [http://www.lankatopjobs.org](http://www.lankatopjobs.org)
cant ping by number also

what IP is the DNS giving you?

---

