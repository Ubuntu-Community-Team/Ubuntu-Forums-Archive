---
title: "DNS server and DynDns"
date: 2010-01-23
forum: General Help
---

### Post by zinv on 2010-01-23
I have just recently started messing around with running a dns server and i was also considering signing up with a dynamic dns service so i could access my computer when im not home. My question is would there be a problem with running a dns server behind the dynamic dns host or would it not be possible?

---

### Post by dcstar on 2010-01-24
> **zinv said:**
> I have just recently started messing around with running a dns server and i was also considering signing up with a dynamic dns service so i could access my computer when im not home. My question is would there be a problem with running a dns server behind the dynamic dns host or would it not be possible?

Your home DNS server (that only serves your internal network) cares little about your external DynDns setup.

---

### Post by Ordes on 2010-01-24
the dns server u setup is is just a home-dns? for your home-network? than it doesnt care...

cuz u when u actually have a registered dns for your "home" u wont need dynDNS anymore...

---

### Post by efflandt on 2010-01-24
It depends what you are trying to do.  Your public IP does not even matter if running local DNS for your LAN and/or caching.  I have been running bind9 on an old Celeron 300 for many years, initially as pppoe/firewall/router/webserver/sshd/etc., but now it sits behind a 2Wire wireless/modem/router.  I have been using no-ip.com for dynamic dns, but rather than tickling them constantly to grab my public IP, I run a Perl LWP script as a daemon that monitors my PPPoE IP on the 2Wire and just notifies no-ip.com if it changes.

I actually have several no-ip.com subdomain names for playing around with name based virtual web hosting.  A one page dead end worm trap is logged separately if an http request does not have one of those names (so worms do not flood my regular logs).

If you intend to do authoritive public DNS for a public domain I am certain that you would need a static public IP.

---

### Post by zinv on 2010-01-24
thank you for your fast replies, i was considering using it just for my home LAN to serve my local machines but i had also wanted to know if it was possible for a public server but efflandt has answered it pretty dead on im thinking so i will just stick to running it for my local network.

---

### Post by meharts on 2010-01-30
Hi zinv;)
I hope you don't think this is toooooooooo cheeky of me...but you have already started a DynDNS thread and I thought we could develop the question a little...please say if you against this....

Any way was hoping to use DynDNS...have before but not for some time now. I have a customer who uses a router set for dhcp and I need to get access to him remotely sometimes...

OK! I have created a DynDNS address to test this at home by putting my customers computer outside of my router...and at DynDNS I have created the address with the ip I want to protect even if broadband update...all well and good. 

I have noticed that there is a DynDNS updater for Linux and wondered if anybody had got that up and running?

I would like any help on this I can get and evem give others reading zin's thread this opportunity to use this updater!

Thanks guys!

meharts

---

### Post by Ordes on 2010-01-30
ddclient..

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

it pretty much walk u through the basic config on installation. And than u can tweak the config if needed.. /etc/ddclient.conf

---

### Post by meharts on 2010-01-30
Hi Ordes:)

Thanks for dropping in! OK! will check out your info and get back to you....

Question:???:

OK! not used, as said, DynDNS for a long time but as a company I am going to have more use for it......

_Scenario_

I have a tendency to waffle on, so I appologise in advance;)

I have a Dir-825 d-link and i have enabled my DynDNS address. On my network at home under "network settings" I have enabled the dhcp server to give out static addresses to my network without me having to personally set them up so.. I can then reserve which addresses I like.

Now on my customers computer when logged into DynDNS it automatically sees  my routers address which is xx.xx.xx.xx

Now I have setup my DynDNS with the reserved address..which for arguments sake is 192.168.0.xxx. I have tried to set up the router so it forwards on that address to my customers computer but must be doing something wrong..

I have setup nx server on customers ubuntu karmic koala and can login now after much .....help from you guys here..from windows with the nomachine client.

I have tried to test the network by getting a friend to login via nomachine from windows with host as DynDNS (192.168.0.xxx)

My friend is getting no such host available? I don't know if it is the missing updater on ubuntu which I am going to look at now?

I also thought that logic says that I can open the port to my computer on the router via virtual servers list ....still not working yet!

Can this be of use to someone else in the future?

meharts

---

### Post by Ordes on 2010-01-30
mhm, ok 

Basics:
1) 192.168.xxx is your internal IP, means the IP given to your PCs inside your network. You cannot use this to connect from the outside

2) Public/ external IP, is the IP you need in order to connect to your system;  >> e.g   checkip.dyndns.org  >> will show you your external IP

3) DHCP vs Static; you should use static IPs; At least for the server machines; You have to assign them one IP like 192.168.2.100; so the router knows where to go; If not static, it might change and your setup wont work anymore


Setup:
1) in ddclient, you have to grab your public IP and set to use for your dyndns... in the link above its the part where is written, 
use=web, web=checkip.dyndns.org .....

2) The router has to know where to go and send the request to when u connect. Thats where the static IP comes in. e,g forward to 192.168.2.100 port 20-21  (which is mostly used in ftp, as an example)

3) You have to allow incoming request in your Linux firewall. If u never configured a linux firewall, i think firestarter is good tool to configure your firewall.
Allow incoming for XXXX on port XXXX  > u dont want to open it for everything >> just for the stuff u need...


Edit: just reread your post
Are you saying that dyndns sees your real public IP, and as an example u used 192.168.1.1 ?
If so, than your public IP is already set up and forwared correctly. The only thing u need to do is setup the internal parts.. Firewall, forwarding etc...
Got confused, cause u replaced your public IP with 192.168...  which is normally an internal and not an external...

But if your dyndns thinks your public IP is actually 192.168.xx.xx than you forwarded your internal IP and not the public one. So it wont work.
check >  checkip.dyndns.org   (in your brwoser) to get an idead about your public IP. You probably also need to setup the internal, like written above

---

### Post by meharts on 2010-01-31
Hi Ordes

Thanks for coming by at the again at the weekend! I will be looking at that today and let you know how it goes...

Thanks a lot for your time;)

meharts

---

### Post by meharts on 2010-01-31
Hi again:)

Well, now I have something I have never encountered before. As said before, I have a D-link dir-825...not an old router by any means...but...now here is the interesting thing.

I had the dhcp server enabled and I reserved the addresses I wanted to keep...when I run sudo ifconfig it gives me both the inbuilt network cards on his P6T Deluxe V2 motherboard. When I looked in the list on my router it gives an address for customers computer with the right mac address...but the address begins with e0: now my router lists the computer and correct mac address......no problem you would think...

I can't reserve the mac address because of it beginning with e0: and what is more interesting is the date it gives for expiery......sept 1927.....you read right:o

I thought my router had gone bananers but it must be that the motherboard is too new for the router?

Going to test the setup to see if DynDNS forwards to the right ip and let you know....don't want to suggest a new network card but if it doesn't register the inbuilt ones I might have to...

meharts

---

### Post by Ordes on 2010-01-31
hard to follow what u trying u do... e.g reserving the mac adress.. where? for what...? pretty sure its not the problem of the hardware, nor is the motherboard to new... pretty sure its just the basic network setup..

---

### Post by meharts on 2010-01-31
Hi again!

Sorry, not trying to confuse anyone...when I enable my dhcp server on my router it has a range for my ip's that I can choose my self....I can also reserve addresses for things like naslite servers which usually have static ip's and I keep tabs on them...

The problem with mac addresses beginning with letters/numbers beginning with anything other than 00: has been brought up on the d-link forum but no solution has been added yet?!!

_**Ordes**_
Your info worked a treat and I thank you for all your help on this matter;)

meharts

---

### Post by Ordes on 2010-01-31
;)  good...

when using dhcp and static together just make sure your dhcp range IPs dont include your static IPs. e.g your statics r xx.xx.xx.100 - ....109 ... so your dhcp starting IP could be xx.xx.xx.110

---

### Post by meharts on 2010-02-01
Hi Ordes:D

OK! thanks for the update. Good point...will bear that in mind.

Thanks again!

meharts

---

