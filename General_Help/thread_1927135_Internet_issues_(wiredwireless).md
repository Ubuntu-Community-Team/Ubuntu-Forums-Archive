---
title: "Internet issues (wired/wireless)"
date: 2012-02-17
forum: General Help
---

### Post by SE7EN-LOCSTA on 2012-02-17
I have built a new computer, and I just got cable internet to go along with it. Everything works fine, except for loading web pages. The issue is very noticeable on Windows7, but it is present in Ubuntu 11.10 also. I have used a wireless PICe card, and also tried the integrated LAN port, but it is there regardless of which I use. I have tried on the router a static Ip, the normal dynamic Ip, DMZ zone.. nothing changes it. 

 I can get on and play Starcraft II and other games online just fine, but trying to load a webpage is horrible. RAM stays at less than 50% and CPU usage is real low. at idle I do have about 90 processes running, most of them are drivers and such. other, slower computers in the house do not noticeably have this problem, so I don't know what to think. 
My thoughts on it so far are:
1. testing with 2 separate adapters, it is not my wireless card.
2. occurring from more than 1 operating system, it is not a windows problem. 
3. being a new system, and occurring on windows AND ubuntu, and having ESET antivirus, and being a new computer with not alot of non-driver programs, it is not malware.
4. RAM/CPU usage is fine, and other programs (including 3d gaming) is running smoothly, so it is not a hardware issue.
5. I am hitting 2.5 mbs [from 20mb cable] on utorrent, so it's not a loss of connection. 

now, those are just my thoughts, and to give anyone that might be able to help some info of things i've tried and what does work, so I may've ruled out something that I shouldn't have. 

The only thing I can think of, and I don't even know if this is feasible... is there someway that I may be overloading my HDD - 500GB 7200 RPM SATAII - and that makes it able to do everything else but give up on loading webpages?

other advice given to me was that it was a DNS issue, and i flushed my DNS on Windows, but it didn't fix the problem. I am stumped. Any help would be nice. Thanks.

---

### Post by belmont52 on 2012-02-17
Try playing with the bios settings, if it isn't an os issue then the next place I would look is the bios.

---

### Post by SE7EN-LOCSTA on 2012-02-17
> **belmont52 said:**
> Try playing with the bios settings, if it isn't an os issue then the next place I would look is the bios.
the only thing I could see in the BIOS about networking was to enable/disable the onboard ethernet port. It's an asus p8z68-v gen3 if anyone has some knowledge about that board.

---

### Post by jonobr on 2012-02-17
When your having your problem with web pages loading did you check if DNS was working ok?


I.e. if you are having an issue with google.com


try running 
```
nslookup google.com
```

[This thread]("http://ubuntuforums.org/showthread.php?t=1925571") is a good example of someones DNS not working correctly showing issues with resolving.

In his case some would not load and some would give an incorrect nslookup

You can see changing to 8.8.8.8 in the dns settings proved it to be a local DNS issue

HTH

---

### Post by SE7EN-LOCSTA on 2012-02-17
The DNS change seems to have helped a bit, but I am still noticing an unreasonable amount of time to load / not loading at all.

---

### Post by jonobr on 2012-02-17
Hello


For not loading at all , you need to try the nslookup I mentioned,

On the speed, I'm thinking given your investigations,
and also that its not OS specific, and given DNS improved things a bit,
Im thinking your router may be about to give up the ghost and may need to be updated or upgraded to a later one?

Maybe you could try on a different network if you have the ability to move around?

---

### Post by jonobr on 2012-02-17
Your very welcome elizabethmc,
thanks for the thanks:D

---

### Post by SE7EN-LOCSTA on 2012-02-17
dns request timed out.
timeout was 2 seconds
server: unknown
address: 8.8.8.8
***request to unknown timed out

I will look into updating firmware, its a new router from the cable company.

---

### Post by HereInOz on 2012-02-17
It does sound a little like slow DNS resolution.  The thing to look for is initial slowness loading the webpage, then once it is loading, it happens quite quickly UNTIL:

The site sends you off to get content from a third party site.  Then the slowness returns while the DNS for the 3rd party site is sorted out, and once that is done, the loading proceeds apace.

If you want to test this with a very simple site, which is basically text and no third party links, try mine - [www.meridiancomputer.com.au](www.meridiancomputer.com.au)

It is a buck basic site and should load in an instant.  If it takes a while to start loading, then loads quickly, you have a DNS resolution issue.

Cheers,

Alan

---

### Post by SE7EN-LOCSTA on 2012-02-17
your site loaded in half a second. that's faster than google.com does.

the problem does seem to come and go though.. now most sites seem to be working fine. 20 minutes ago, not so much. (but it is USUALLY for the worse)

---

### Post by HereInOz on 2012-02-17
Ok, so it is not a DNS resolution issue.  Half a second is about right.

Although if it is intermittent, it could be delays accessing your DNS server.

---

### Post by HereInOz on 2012-02-17
Try going in to Windows 7 and set your IPv4 network properties to use the following DNS servers:

208.67.222.222
208.67.220.220

They are the OpenDNS servers, and if that makes a difference, or increases the consistency of the whole thing, then it is indeed DNS related.

I am assuming you are still using an IPv4 modem/router?

---

### Post by jonobr on 2012-02-17
almost sounds like a bad cable or port,
or could be something up between you and your isp

---

### Post by SE7EN-LOCSTA on 2012-02-17
ok, the other DNS numbers made it worse, and the only page I was able to open without 3+ tries is google. I had to switch back to 8888 + 8844 to load this site. the google ones are still slow most of the time, but are better by far than default and opendns.

also, this go around, the site you sent me to test with took @4-5 seconds to pull up.

---

### Post by HereInOz on 2012-02-17
Almost sure that you have an intermittent DNS issue, particularly if the site had no action for about 4 seconds, then flashed up within a half second or so.  If that is the case, then it is a probable DNS issue somewhere.

If it started to load fairly quickly, but took 4 - 5 seconds to complete, then it is a network/internet speed issue

---

### Post by SE7EN-LOCSTA on 2012-02-17
> **HereInOz said:**
> Almost sure that you have an intermittent DNS issue, particularly if the site had no action for about 4 seconds, then flashed up within a half second or so.  If that is the case, then it is a probable DNS issue somewhere.

If it started to load fairly quickly, but took 4 - 5 seconds to complete, then it is a network/internet speed issue

It just sat there for like 4 seconds, nothing on screen, saying connecting to.... then bam it was loaded

---

### Post by HereInOz on 2012-02-17
The only thing to do now is to get another computer, connect it in to your network, and see if it has the same issues.  If it does, then it is clearly a problem with your network infrastructure serving out the DNS resoution.

If the other computer is fine, then you have some weird and wonderful fault with your new computer - something like a fault in the PCI bus, south bridge chipset or similar.  

Had one like this recently where we had two network adaptors, one on board and the other PCI card, and both would report 'cable unplugged'.  Didn't matter what we did. Using a USB wireless device worked around the problem, but the issue was somewhere in the motherboard.  Replaced the board - problem solved.

Go and find a friend with a laptop, and see if they have the same issues with your network.

---

### Post by SE7EN-LOCSTA on 2012-02-19
I do have a laptop in the house, and it has the same problem, just much less noticeable. 
The router is broken, it will no longer allow any computer to connect to it at all. Hopefully the issue is just a bad router and not internal computer problems, but I will find out for sure (hopefully) Monday when they bring me a new router. And an N one, since they lied and said the first one was when it wasn't.

Update, New router, everything works great.

---

