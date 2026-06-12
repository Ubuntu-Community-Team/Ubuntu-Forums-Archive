---
title: "extremely slow internet"
date: 2009-11-03
forum: General Help
---

### Post by quimkaos on 2009-11-03
i'm having trouble with firefox! i'm geting an extremely slow internet, not in download speed but in opening any site. from time to time (less then 10mn intervals) firefox goes berserk  and takes 5 mn to open any site, with messages in status bar like: "resolving server xxxx.com", "waiting for xxxx.com" or connecting to "xxxx.com". sometimes i get a blank page, others i get an error page but the tab in firefox still says loading, and other strange things like this....

how can i debug/diagnose what's going on?
any thoughts about solving this? anyone has come across this? 

i have this problem since the fresh install of 9.10 but thought that was an minor glitch that would be easily fixed with updates. now it's geting worse ...

---

### Post by SteveDee on 2009-11-03
If you are using Wifi it may be due to a drop in your bitrate as a result of this problem: [http://ubuntuforums.org/showthread.php?p=8224384#post8224384](http://ubuntuforums.org/showthread.php?p=8224384#post8224384)

---

### Post by demonic_crow on 2009-11-03
I'm having the same problem every since I updated.  My firefox even close on me for no reason too.  I hope this get fix cause using firefox with ubuntu was faster then internet explorer with windows.

---

### Post by skylark on 2009-11-03
Sounds like it is slow at the DNS lookup stage. There are some decent tips to diagnosing a similar problem at: [**_http://richs-lxh.linux-hardcore.com/tag/connection/_**]("http://richs-lxh.linux-hardcore.com/tag/connection/")
If you do a search of the forums you might also find some good tips. You might find some helpful info [**_in this thread_**]("http://ubuntuforums.org/showthread.php?t=1130252&page=2").

Good luck!

---

### Post by quimkaos on 2009-11-03
not using wi-fi connection... standard wired 10/100/1000 card connected over a Zyxel P334 router with cable connection of 8Mb/s and using DHCP.

and yes seams more to be an dns problem, tho at windows it works perfectly, so the problem shouldn't be from router side.

---

### Post by quimkaos on 2009-11-03
well i did this:
in networkManager, Edit your connection profile, IPv4 tab. Change from "Automatic (DHCP)" to "Automatic (DHCP) addresses only", and enter your DNS information manually.

i used has primary DNS my router, meaning that it will be my router managing my DNS. i think this is fine since the router is my DHCP server. this is also usualy what is done in windows machines...

---

### Post by HiImTye on 2009-11-03
> **quimkaos said:**
> well i did this:
in networkManager, Edit your connection profile, IPv4 tab. Change from "Automatic (DHCP)" to "Automatic (DHCP) addresses only", and enter your DNS information manually.

i used has primary DNS my router, meaning that it will be my router managing my DNS. i think this is fine since the router is my DHCP server. this is also usualy what is done in windows machines...
this worked for me

---

### Post by quimkaos on 2009-11-03
and until now everything works in flash mode!

---

### Post by QwUo173Hy on 2009-11-03
So if my routers IP is 192.168.1.1, I used this for my DNS?

---

### Post by quimkaos on 2009-11-03
yes... then the router will use the dns from your isp...

---

### Post by svref on 2009-11-03
You and I may have the same problem. I'm already using my router as my DNS resolver, and the Apple across the way is not having the same problem as I am (I imagine it uses the same DNS too).

Try timing your DNS queries by typing the line "time host localhost" into a terminal. Mine takes 10.07 seconds, which is 10.00 too long. As detailed here: [http://ubuntuforums.org/showthread.php?t=1312883](http://ubuntuforums.org/showthread.php?t=1312883)

---

### Post by QwUo173Hy on 2009-11-03
Thanks for clarifying quimkaos. 

svref, I had the same timings as you until I added the DNS information as mentioned. Now I get: 0m0.152s

I'm pretty clueless when it comes to networking and wireless, but should a bug be filed against.. something?

---

### Post by Green_Star on 2009-11-04
> **quimkaos said:**
> well i did this:
in networkManager, Edit your connection profile, IPv4 tab. Change from "Automatic (DHCP)" to "Automatic (DHCP) addresses only", and enter your DNS information manually.

i used has primary DNS my router, meaning that it will be my router managing my DNS. i think this is fine since the router is my DHCP server. this is also usualy what is done in windows machines...

It worked for me, thanks.

---

### Post by quimkaos on 2009-11-04
well... i started with everything dynamic... then changed "dns servers"... now i'm using fixed IP name server and gateway cause seams i cant rely in ubuntu default configs...

---

