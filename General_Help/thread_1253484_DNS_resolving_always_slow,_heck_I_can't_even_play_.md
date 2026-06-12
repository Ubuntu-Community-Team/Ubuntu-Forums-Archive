---
title: "DNS resolving always slow, heck I can't even play game!"
date: 2009-08-30
forum: General Help
---

### Post by samuel.faith on 2009-08-30
Hi folks,

I am using Jaunty, recently updated to kernel 2.6.28-15-generic. Installed on new Dell Inspiron 1440.

Here is the deal. The problem I am encountering is, the Internet on my Ubuntu is always freaking slow. Ok, it's not slow. Let me reword it. Whenever it's looking up/attempting to resolve a DNS, it takes so long. I don't know how long, since I don't think it's practical to use my watch to time it.

So when I listened to my connection using Wireshark, I found this. The rest comes ok, but whenever there is a DNS query, it takes sometimes, always.

It's like, momentary pause (noticeable pause, mind you) while doing DNS query or something, and then burst of data, then again another pause, then burst of data.

Whenever it is doing DNS query thingie, it always interrupt the flow of data. I mean whenever I am surfing website or streaming music from IMEEM, or anything else online, the connection will simply stop.

This is really annoying especially whenever I try to play EVE Online or Guild Wars, or any other games using WINE. Please note that this didn't happen two months ago, when I had no problem at all. Is it because of the kernel upgrade?

I have no problem on Vista on the same lappy, which is weird since like I said, until two months ago, Ubuntu was always faster in Internet surfing. And every other Windows boxes  and lappies in my house on same network? No problem at all.

If you are going to suggest me to use OpenDNS, trust me, it's been done. I am using OpenDNS for the whole home network. And on my lappy, it's configured to use OpenDNS for whatever connection.

Disabling IPv6 on Firefox doesn't help much either. I notice a slight improvement in pages loading in Firefox, but it doesn't help in others, like playing MMOs.

When I was searching in Google, I found a way to blacklist IPv6, but I am not certain if it will work with this new kernel version (some websites stated it won't), and I am not certain if I will need IPv6. I am in Singapore, and using Starhub MaxOnline cable service.

My Jaunty started updating the kernel since about two months ago (that time was not 2.6.28-15 yet, I believe), since then the problem started. To be exact, until second week of July, it worked just fine.

I have no other problems using Jaunty. I am a technical person, a front-end developer and UX designer, with a bit of know-hows in my head when it comes to networking. The bottomline is, I am not a complete newbie. But yeah, in this case, I feel like a complete idiot.

Hmm... if this problem cannot be fixed by myself using any methods, I really hope when 9.10 comes out, it will be fixed.

If any one of the geniuses here have a workaround for this problem, I'd really appreciate it.

Thanks for reading this long-winded rant, folks!

Sam

---

### Post by samuel.faith on 2009-08-31
Bump

(please please... no one?)

---

### Post by scradock on 2009-08-31
Don't hold your breath - it is still like that in Karmic (eventually to be 9.10). Are you using Firefox 3.5? I have heard it has some new database system for holding DNS lookups in, but maybe it isn't working right yet. At any rate, it takes soooo long to look up a simple DNS record, even after disabling ipv6, as you say.....

---

### Post by mike555 on 2009-08-31
try "open dns"  ... [http://www.opendns.com/](http://www.opendns.com/)

---

### Post by samuel.faith on 2009-08-31
> **mike555 said:**
> try "open dns"  ... [http://www.opendns.com/](http://www.opendns.com/)

Perhaps you are not reading my post properly. I am using OpenDNS ATM. But it doesn't resolve the problem.

---

### Post by samuel.faith on 2009-08-31
> **scradock said:**
> Don't hold your breath - it is still like that in Karmic (eventually to be 9.10). Are you using Firefox 3.5? I have heard it has some new database system for holding DNS lookups in, but maybe it isn't working right yet. At any rate, it takes soooo long to look up a simple DNS record, even after disabling ipv6, as you say.....

So isn't there any solution yet? I have tried Firefox 3.5 but it's not working like Firefox 3.5 in Windows or Firefox 3.0.13 in Ubuntu.

My problem is not just with Firefox, but with all Internet connections, even SSH. The problem is more prominent when I play MMOs, like EVE or Guild Wars.

Imagine the whole thing stop when I am in the middle of heated fleet battle in EVE, or in a raid in Guild Wars.

OK, maybe gaming is not so important. But what about SSH? What about other works I have to do on the web? I am a front-end developer, and UX designer. Most of the works I do are online.

This is totally unacceptable. I am using Ubuntu because it's darn a lot better than Windows in every single aspects I can see. I bought Guild Wars not just because it's a great fantasy MMO, but also because I can play it flawlessly on Ubuntu. I started trying EVE because it is a great MMO also available for Linux.

But now, if this problem persists, I may have to fall back to using Windows for my MMOs. But then what's the point? I want to make a complete switch to Ubuntu. But now ... :(

---

### Post by CatKiller on 2009-08-31
For the record, I was also having slow DNS lookups with Jaunty when using my ISPs DNS servers. Switching to OpenDNS fixed it right up. So it's not quite as widespread a problem as you might fear. I did configure my router with the OpenDNS servers rather than just the computers, which might be a step that you haven't done.

---

### Post by falconindy on 2009-08-31
> **samuel.faith said:**
> I am a technical person, a front-end developer and UX designer, with a bit of know-hows in my head when it comes to networking. The bottomline is, I am not a complete newbie. But yeah, in this case, I feel like a complete idiot.
If you suspect the kernel, why not compile and install a prior kernel release? Also, have you tried **not** using OpenDNS?

Just out of curiosity, are you on wireless? It sounds like you are. Also sounds like your NIC driver changed and duplexing was turned off.

---

### Post by samuel.faith on 2009-08-31
> **CatKiller said:**
> For the record, I was also having slow DNS lookups with Jaunty when using my ISPs DNS servers. Switching to OpenDNS fixed it right up. So it's not quite as widespread a problem as you might fear. I did configure my router with the OpenDNS servers rather than just the computers, which might be a step that you haven't done.

> **falconindy said:**
> If you suspect the kernel, why not compile and install a prior kernel release? Also, have you tried **not** using OpenDNS?

Just out of curiosity, are you on wireless? It sounds like you are. Also sounds like your NIC driver changed and duplexing was turned off.

Oh darn, I'd be so darned if Ubuntu God hears all my rants and whines.

@falconindy, (nice name, btw) I just turned off OpenDNS, from both my router and my lappy. As I am on Starhub, I went for a less laggy and less known DNS server from my ISP. And bingo! The issue just went away. It became non-noticeable by a human, although delay while DNS resolving is still showing in Wireshark logs.

I will try recompiling an old kernel release on my test machine, thanks for the advice. Let's see how it goes, with and without OpenDNS on old kernel.

Yes I am on wireless, and what's it with duplexing thing? Would you mind to elaborate, Indy ( or shall I call Falcon? ;> )?

@CatKiller, I have OpenDNS on both my router and lappy, router for the sake of benefit for all people in my house, and lappy for myself when I am on other connections. Looks like OpenDNS seems to be a problem, which I find it weird. By the way, I love cats, man. ^_^

Anybody here from Singapore using Starhub Maxonline Ultimate? It promises to be 100mbps, which I know we won't get it, but from time to time their connection slows down and it is really irritating.

UPDATE: Just for Starhub users here, I just changed my DNS in my lappy to use Singtel DNS, which seems to be a lot faster than Starhub DNS servers. I am still thinking if I should use that in my router configuration as well, not certain about the potential complications though.

Singnet DNS servers are: 165.21.100.88 an 165.21.83.88; the latter one seems to be faster when I ping it. Compare both of them to Starhub DNS, they are still slightly faster, at least in ping results.

Folks, thanks a lot for reading through my long-winded rants :D. I appreciate everyone trying to help me, truly OSS spirit!

Sam

---

### Post by falconindy on 2009-08-31
> **samuel.faith said:**
> @falconindy, (nice name, btw) I just turned off OpenDNS, from both my router and my lappy. As I am on Starhub, I went for a less laggy and less known DNS server from my ISP. And bingo! The issue just went away. It became non-noticeable by a human, although delay while DNS resolving is still showing in Wireshark logs.

I will try recompiling an old kernel release on my test machine, thanks for the advice. Let's see how it goes, with and without OpenDNS on old kernel.

Yes I am on wireless, and what's it with duplexing thing? Would you mind to elaborate, Indy ( or shall I call Falcon? ;> )?
It's a little "suspicious" that you had OpenDNS configured on both your router **and** your laptop. You should only need to configure it on the router, and then let your laptop take its DNS parameters from upstream (the router).

Duplexing is the ability of a network device to send and receive at the same time. Back in the days of coax connections (10Base-T), suplex connections were more common -- you could send and receive, but not at the same time. If you tried to download and upload, you'd be interrupted as the NIC tried to juggle both operations. Still, the ability to duplex is dependent on the driver as well as the physical NIC. 

I mentioned the wireless because well... that's generally been my experience with wireless connections that weren't wi-fi hotspots (e.g. airports or college campuses). Also, because I presume that you haven't recompiled your kernel before, you'll want to make sure that when you DO recompile, you enable minstrel as the rate control algorithm. I don't recommend you follow [this guy's directions for recompiling]("http://izanbardprince.wordpress.com/2009/03/26/how-to-fix-ubuntu-jaunty-warning-hacks-ahead/"), but he has information on how to enable this particular algorithm in the kernel. I **would**, however, recommmend [this blog]("http://blog.avirtualhome.com/2009/04/29/how-to-compile-a-kernel-for-ubuntu-jaunty/") for tips on recompiling.

Thanks, most people shorten my tag to Falc. It's short for the name I do my business under, Falcon Industries.

---

### Post by ballison78 on 2009-11-18
This fixed my problem: [http://crimm.me/2009/10/slow-dns-lookups-on-ubuntu-910.html](http://crimm.me/2009/10/slow-dns-lookups-on-ubuntu-910.html)

I almost gave up on Ubuntu because of this bug but then I tried Fedora and it was just as bad.

---

### Post by Arup on 2009-11-18
You can also install pdnsd which will store all the dns lookups locally for instant dns fetch. 

[http://ubuntuforums.org/showthread.php?t=331850&page=4](http://ubuntuforums.org/showthread.php?t=331850&page=4)

Follow jontysell's instructions, works quite nice.

---

### Post by crucialhoax on 2009-11-18
I installed Wicd Network Manager, and I added 2 of the main OpenDNS servers into the settings of my connection. Speed went from 50kb/s to 2.3mb/s :)

Hope this helps.

---

