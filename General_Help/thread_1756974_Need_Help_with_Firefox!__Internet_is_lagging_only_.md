---
title: "Need Help with Firefox!  Internet is lagging only in firefox!"
date: 2011-05-12
forum: General Help
---

### Post by dbrannon79 on 2011-05-12
Hello,  I have been using Ubuntu 10.10 for a while now and everything has worked 10 times better than windows 7.  until recently all had been good, for the past few weeks my Internet has been slowing down.  I did some checking and even called a service tech from my ISP and they said that is was my laptop.  for a while I did not believe them.  but now I am convinced that its something in ubuntu that is making the Internet slow.

I tried using my old desktop that runs windows xp and the net is faster than the laptop.  In the past I have had this trouble in windows 7 and firefox.  to fix the problem I simply backed up my bookmarks and un-installed firefox, then did a clean install.  after that all was good for a while.   I attempted to to the same in Ubumtu, opening the software center and removed firefox. then re-installed it from the same software center.  when I open firefox, it had retained all mf my bookmarks, homepage and other settings which told me that I didn't completely remove it.

How can I completely remove all of firefox and do a fresh install in order to verify that firefox is not causing my Internet trouble?

---

### Post by lovinglinux on 2011-05-13
Removing Firefox doesn't remove your settings.

I would start by disabling ipv6, instead of deleting all your stuff. Most likely it will fix your problem. You can also enable pipelining and applying other network tweaks. See [http://www.webgapps.org/firefox/preferences-tweaks](http://www.webgapps.org/firefox/preferences-tweaks)

If that doesn't help, you can delete your Firefox profile to completely reset it. But I would advice to first create a new profile and test it, before deleting anything.

See [http://www.webgapps.org/firefox/fixing-corrupted-profiles](http://www.webgapps.org/firefox/fixing-corrupted-profiles)

---

### Post by lithopsian on 2011-05-13
Quick way to test Firefox without things you have changed:
firefox --safe-mode

How to create a brand new clean and empty profile for testing (without losing your current profile):
firefox -P

Fingers crossed either of those will restore your browsing to its former speed.  Then, if you like, we can work to narrow down what has gone wrong in your profile.

---

### Post by dbrannon79 on 2011-05-13
Thanks for the tips,  I will try this tonight and see what happens.  creating a new profile had never crossed my mind :)  I'll try to post the results later tonight.

Thanks.

---

### Post by dbrannon79 on 2011-05-13
some additional info that might narrow down what might be going on...  in most all cases when a page is loaded, firefox will sit there for a while with the bottom of the screen showing "looking up http:....."  or "loading..."  all while the page stays blank.  once im guessing it finds the page, it loads it promptly.  I also tried speedtest.net and the wait for the page to loag took a few, but once it loaded and I ran the test, the results did not show any problems. 13+ mbps down and .54+ up and 64+ ms ping??  
I was thinking it was a dns problem but the other desktop uses the same router!

---

### Post by lovinglinux on 2011-05-13
> **dbrannon79 said:**
> some additional info that might narrow down what might be going on...  in most all cases when a page is loaded, firefox will sit there for a while with the bottom of the screen showing "looking up http:....."  or "loading..."  all while the page stays blank.  once im guessing it finds the page, it loads it promptly.  I also tried speedtest.net and the wait for the page to loag took a few, but once it loaded and I ran the test, the results did not show any problems. 13+ mbps down and .54+ up and 64+ ms ping??  
I was thinking it was a dns problem but the other desktop uses the same router!

Could be a DNS problem, however is more likely to be the ipv6 issue. Just disable ipv6 and it will speed up.

---

### Post by dbrannon79 on 2011-05-14
ok, I disabled the ipv6 and created a new profile in firefox, and still no go!  now i am not so sure its actually firefox, I installed chromium browser and google chrome.  both browsers do the same thing.  I also booted into backtrack4 which is installed on this same laptop and the internet works fine there.  there must be something in the network settings in ubuntu that is causing the trouble. if I try to access my routers ip menu, it also loads slowly.  what are some things I can check?

---

### Post by lovinglinux on 2011-05-14
> **dbrannon79 said:**
> ok, I disabled the ipv6 and created a new profile in firefox, and still no go!  now i am not so sure its actually firefox, I installed chromium browser and google chrome.  both browsers do the same thing.  I also booted into backtrack4 which is installed on this same laptop and the internet works fine there.  there must be something in the network settings in ubuntu that is causing the trouble. if I try to access my routers ip menu, it also loads slowly.  what are some things I can check?

I actually never had any network issues with Ubuntu, so I don't know where to start. But I would check for MTU and QoS in the router.

---

### Post by Whiteice on 2011-05-14
dbrannon79 you can always try this I don't know if the newer versions of firefox will let you but back in the day this made a 110% difference. just follow the instructions on the link [HTML]http://blog.brainstormbrand.com/productivity/2007/04/9-steps-to-speed-upbroadband-firefox-browsing[/HTML]

---

### Post by dbrannon79 on 2011-05-14
> **lovinglinux said:**
> I actually never had any network issues with Ubuntu, so I don't know where to start. But I would check for MTU and QoS in the router.

in the router the MTU is set to auto with 1500 greyed out,  do I need to change that setting?
the QoS is disabled.
The router is a linksys wrt54g with dd-wrt installed..

I changed my dns settings to use opendns service instead of using google's dns.  I did notice that after disabling the ipv6, the google homepage loads quick and searches in google show instantly now, but when I click on a link from the search it takes it's time loading. I choose speedtest in a search them clicked on the first link which was speedtest.net.  it showed "looking up www.speedtest.net" for a moment and then began to load.  took about  1 1/2 min to load.  clicked begin test and my results came back 32ms ping, 14.08 mbps down and .46 up
the trouble is finding the page, seeming like ones the pc finds the page, it loads with no trouble.  what takes long is when pages are loaded that have the browser look up several pages to get info.  that's why I thought it was the dns problem, but can't figure that out when this pc is the only one having the trouble!   

if dns settings are set in ubuntu, where can I look to see maybe they are conflicting with the router!
or maybe other settings are having conflicts!

---

### Post by lovinglinux on 2011-05-14
> **dbrannon79 said:**
> in the router the MTU is set to auto with 1500 greyed out,  do I need to change that setting?
the QoS is disabled.
The router is a linksys wrt54g with dd-wrt installed..

I changed my dns settings to use opendns service instead of using google's dns.  I did notice that after disabling the ipv6, the google homepage loads quick and searches in google show instantly now, but when I click on a link from the search it takes it's time loading. I choose speedtest in a search them clicked on the first link which was speedtest.net.  it showed "looking up www.speedtest.net" for a moment and then began to load.  took about  1 1/2 min to load.  clicked begin test and my results came back 32ms ping, 14.08 mbps down and .46 up
the trouble is finding the page, seeming like ones the pc finds the page, it loads with no trouble.  what takes long is when pages are loaded that have the browser look up several pages to get info.  that's why I thought it was the dns problem, but can't figure that out when this pc is the only one having the trouble!   

if dns settings are set in ubuntu, where can I look to see maybe they are conflicting with the router!
or maybe other settings are having conflicts!

Google DNS never really worked for me. I use the DNS of my ISP.

For the MTU, try to change it to 1492 if possible. I have seen several posts from users having network issues, that changing from 1500 to 1492 solved the problem.

Also enable QoS and check if it makes any difference.

---

