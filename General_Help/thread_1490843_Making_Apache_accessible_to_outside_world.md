---
title: "Making Apache accessible to outside world"
date: 2010-05-22
forum: General Help
---

### Post by ManiDhillon on 2010-05-22
Okay friends here I’ll try to explain the scenario to the best of my abilities so that you can provide me a solution.

Set Up:
1. Ubuntu 10.04 x64 on Acer Aspire NoteBook.
2. LAMP installed
3. Using an ADSL modem to connect to internet, make is “Nokia Siemens Residential Router 1600“
4. Modem LAN settings are as shown in the attachment picture.
5. So mostly my laptop is assigned the ip ranging from 10.0.0.2 to 10.0.0.10 as the router use NAT.
6. [http://localhost](http://localhost), 127.0.0.1, 10.0.0.2 or whatever my ip is, work fine to see my default Apache homepage in locally connected devices.
7. The ip which I find from [http://www.whatismyip.com](http://www.whatismyip.com) should connect to my Apache homepage but instead it connects to my Router Interface/Configure panel as shown in image attached.

What I want:
1. My Apache home page accessible to outside world via my dynamic ip.

---

### Post by Nythain on 2010-05-22
thats your routers LAN address... you need its WAN address

---

### Post by lisati on 2010-05-22
Have you set your router to forward port 80 to your server?

---

### Post by ManiDhillon on 2010-05-22
> **Nythain said:**
> thats your routers LAN address... you need its WAN address
Yes I know that 10 series is LAN address of my router, It use NAT to convert public addresses to private ip address. The problem is that the private dynamic ip assigned to me which I find through whatismyip.com (117.197.16X.XXX) connects to my router interface.

---

### Post by Nythain on 2010-05-22
ok, well, if whatismyip is giving you the proper outside ip address, then its a simple matter of forwarding port 80 from your router to your internal LAN ip as mentioned by someone else.

also, most routers have an option to connect to dyndns (and other services) at intervals and update that information... and even if your router doesnt, most services offer small packages to do it for you (i personally run noip2 as i use no-ip.com for my dyndns service)

other than the forwarding of the port there shouldnt be any problems

---

### Post by ManiDhillon on 2010-05-22
> **lisati said:**
> Have you set your router to forward port 80 to your server?
I haven't. Let me see if it makes any difference.

---

### Post by ManiDhillon on 2010-05-22
> **Nythain said:**
> ok, well, if whatismyip is giving you the proper outside ip address, then its a simple matter of forwarding port 80 from your router to your internal LAN ip as mentioned by someone else.

also, most routers have an option to connect to dyndns (and other services) at intervals and update that information... and even if your router doesnt, most services offer small packages to do it for you (i personally run noip2 as i use no-ip.com for my dyndns service)

other than the forwarding of the port there shouldnt be any problems

I was just going to forward the port 80, and yes my router support dyndns.com and toz.But I haven't tried that and neither did I know that it would make any difference. Let me check it. Thanks for quick replies. I'll post the progress soon.

---

### Post by lisati on 2010-05-22
> **ManiDhillon said:**
> I haven't. Let me see if it makes any difference.

Let us know how you get on. 
On my router I had to tell it to forward port 80, and I also set it to automatically update the dyndns/no-ip info (mentioned by Nythain) as well. 
(Side note: It's a pity my router can only handle only DNS update service at a time, I used two different providers....)

---

### Post by ManiDhillon on 2010-05-22
Take a look at the attachments. Am i right in putting all the values?

---

### Post by Nythain on 2010-05-22
looks about right to me... any luck?

---

### Post by ManiDhillon on 2010-05-22
> **Nythain said:**
> looks about right to me... any luck?
Well that's the problem dude! No luck at all. Restarted router and still no luck.

---

### Post by ManiDhillon on 2010-05-22
Any other ideas guys?

---

### Post by Nythain on 2010-05-22
so the ip you are putting into your web browser is the WAN ip right... not the 10.0.0.x address??? because if tahts the case, i would probably switch providers or buy a new router/modem anyways, because that means srsly, anyone on the entire internet can access your router right now

---

### Post by efflandt on 2010-05-22
Most routers do not do loopback, LAN2LAN via WAN IP.  To test it from the internet, you have to test it from an internet host (wget or lynx on a *nix shell account somewhere), or dial up or mobile data from a computer not on your LAN.

---

### Post by Nythain on 2010-05-22
dont know if id say "most" since i've failed to encounter a router yet of just about every major brand that didnt allow me to type my external ip address from my own computer and be directed to my webserver... that would make web development and maintenance very difficult if i couldn't access my website from my computer using my no-ip/wan/external ip

---

### Post by ManiDhillon on 2010-05-22
> **Nythain said:**
> so the ip you are putting into your web browser is the WAN ip right... not the 10.0.0.x address??? because if tahts the case, i would probably switch providers or buy a new router/modem anyways, because that means srsly, anyone on the entire internet can access your router right now
I am using the WAN adress but to no avail.
I asked my friend to put in my wan ip into his browser a few secs ago and he couldn't connect to me, not even the Router Prompt. That means I am safe as you told. But why isn't it working?


> **efflandt said:**
> Most routers do not do loopback, LAN2LAN via WAN IP.  To test it from the internet, you have to test it from an internet host (wget or lynx on a *nix shell account somewhere), or dial up or mobile data from a computer not on your LAN.

You are right, I get my router login promt everytime I put my external ip. But nobody else can connect to my ip at all. Where is the problem??

---

### Post by Nythain on 2010-05-22
at this point, im clueless... though a quick google search revealed more than a few people having port forwarding issues with your modem/router, the first resolution i found being, put yourself in the DMZ, but that should really be a last resort

---

### Post by ManiDhillon on 2010-05-22
> **Nythain said:**
> at this point, im clueless... though a quick google search revealed more than a few people having port forwarding issues with your modem/router, the first resolution i found being, put yourself in the DMZ, but that should really be a last resort
Ah but I have already done that to use Transmission BitTorrent. :(

---

### Post by Nythain on 2010-05-22
then, possibly your isp is blocking port 80 on residential accounts to keep you from running a webserver using their bandwidth

if you are already the DMZ, then you shouldnt have to forward port 80, because you're already outside the NAT/Firewall

---

### Post by ManiDhillon on 2010-05-22
> **Nythain said:**
> then, possibly your isp is blocking port 80 on residential accounts to keep you from running a webserver using their bandwidth

if you are already the DMZ, then you shouldnt have to forward port 80, because you're already outside the NAT/Firewall
That means I am out of Luck!!

---

