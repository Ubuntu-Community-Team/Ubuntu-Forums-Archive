---
title: "Windows Vista running faster than Ubuntu 9.04? am i going crazy?"
date: 2009-08-18
forum: General Help
---

### Post by SchindlerShadow on 2009-08-18
alright let me explane, i have a dell inspiron 1525 that was shipped with windows vista, i understand that this laptop also comes with ubuntu if you chose so, i took that out and installed ubuntu, this was a long time ago, its been 2 years now and i have had many os's on my laptop, wich i seem to reinstall everything every week :P well the past week i desiced to have ONLY ubuntu 9.04 and i was working with that, everything was fine, i know my way around ubuntu, but my frends keept egging me on to duelboot so i can play online games with them, i had to chose beetween the 3, windows xp, vista, or 7 rc, i ruled out 7 cuz it dosent support all the game, and my copy of xp is bad, got screached, so even tho i hate vista, i decided thats wat i have 2 do, so i make a partition and install vista, done, reload grub, done, edit grub, ok. so, now it seems that windows vista is MUCH FASTER than ubuntu! and i mean everythings faster, the apps load faster, the internet is faster (somehow)... so.. is their any resonable explanation for this? on ubuntu my ram is only 7% used idle, on vista its 28% these are my spces, 15.5in widescreen, 2ghz pentium dualcore, 4gb ram, bouth 32bit ubuntu and 32bit windows vista, x3100 intergrated vid card, and intel wifi. 

Any Logical explanation? :confused: :confused: :confused:

---

### Post by matthewbpt on 2009-08-18
Hmm well with my hp laptop, Vista flew on it when it was freshly installed, I remember being impressed with its responsiveness etc, but after a month of normal use the boot time had slowed to a crawl, ram usage had increased to 50% on idle, applications took ages to start up, while Ubuntu which I had installed too was still working at exactly the same speed and responsiveness as the day I installed it. I restored my Vista partition to see how it would be and again it was good at the beginning, but after a while it grinded to a halt. Thats my experience with it, while Vista may seem faster at first, its lack of stability means that wont be able to stay that way for long.

Edit: also you may benefit from installing the Dell Ubuntu image, I'm not sure but I think it has Dell specific optimizations for its hardware [http://linux.dell.com/wiki/index.php/Ubuntu_9.04](http://linux.dell.com/wiki/index.php/Ubuntu_9.04)

---

### Post by CatKiller on 2009-08-18
There's a fairly widely documented performance regression with Intel graphics on Jaunty. It's even in the [Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards").

---

### Post by SchindlerShadow on 2009-08-18
> **matthewbpt said:**
> Hmm well with my hp laptop, Vista flew on it when it was freshly installed, I remember being impressed with its responsiveness etc, but after a month of normal use the boot time had slowed to a crawl, ram usage had increased to 50% on idle, applications took ages to start up, while Ubuntu which I had installed too was still working at exactly the same speed and responsiveness as the day I installed it. I restored my Vista partition to see how it would be and again it was good at the beginning, but after a while it grinded to a halt. Thats my experience with it, while Vista may seem faster at first, its lack of stability means that wont be able to stay that way for long.

Edit: also you may benefit from installing the Dell Ubuntu image, I'm not sure but I think it has Dell specific optimizations for its hardware [http://linux.dell.com/wiki/index.php/Ubuntu_9.04](http://linux.dell.com/wiki/index.php/Ubuntu_9.04)

wow thx, i didn't know their was one just for dell computers, and yea i know it slows down over time, but i reinstall every month anyway lol but ima give that dell iso a try :lolflag:

---

### Post by P4man on 2009-08-18
Matthew is right. Windows is pretty fast with a fresh install, but try it for a few months..  I installed windows 7 a while back, and was thoroughly impressed by it. Then I installed all the stuff I needed (drivers, plugins, office stuff, java, flash, .. an A/V, some utilities) and speed dropped back to being. well, still quite reasonable. 2 months later its becoming slow.

Application speed.. well, try and quantify. But if eg firefox is faster, then thats hardly a miracle if you have a months old install with all your bookmarks, history and plugins versus a vanilla install.

That said, some things shouldn't be faster on windows or different on any OS, like "internet". I assume download speeds are similar, but if there is a difference in "response time" while browsing? If so check if you don't have IPv6 enabled:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Also run "top" on ubuntu and see if there isn't something hogging your system.

---

### Post by Commander_Keen on 2009-08-18
So I noticed the same thing, I have an Insprion 1100 ( I think)
2.4ghz, 1gb of ram.
and XP is much faster then Ubunto.

---

### Post by philinux on 2009-08-18
I just reinstalled xp on my GF's pc. It took an age to boot and an age to login to get to a usable desktop.

It now flies. Seconds to login window and seconds to usable desktop. But like has been said this effect wont last long.

---

### Post by SchindlerShadow on 2009-08-18
> **P4man said:**
> Matthew is right. Windows is pretty fast with a fresh install, but try it for a few months..  I installed windows 7 a while back, and was thoroughly impressed by it. Then I installed all the stuff I needed (drivers, plugins, office stuff, java, flash, .. an A/V, some utilities) and speed dropped back to being. well, still quite reasonable. 2 months later its becoming slow.

Application speed.. well, try and quantify. But if eg firefox is faster, then thats hardly a miracle if you have a months old install with all your bookmarks, history and plugins versus a vanilla install.

That said, some things shouldn't be faster on windows or different on any OS, like "internet". I assume download speeds are similar, but if there is a difference in "response time" while browsing? If so check if you don't have IPv6 enabled:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Also run "top" on ubuntu and see if there isn't something hogging your system.

im starting to think that Microsoft did this on purpose... :(

---

