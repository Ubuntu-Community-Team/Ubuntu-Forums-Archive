---
title: "Internet and Network Problems (Slow)"
date: 2006-03-08
forum: General Help
---

### Post by wilryt2 on 2006-03-08
Currently, I have just installed Kubuntu 5.10, and am attempting to configure my networks.  This question is regarding my built in wired network.  It is working, but only partially.  I can connect to my router fine.  I can ping my router, and all other computers on our network with pings of less than 1ms, but when I ping [www.google.com](www.google.com), it is upwards of 2000ms.  When I surf the internet, it takes about 2 minutes to load a page.  When on windows on this computer, and any other computer on the same network, loading a page seems instantaneous.

What should I look for in my configurations?

What should I post so you have all the information needed to help troubleshoot?  

I am relatively new to the linux world, but hope to become a contributing member of the community.  Thanks for all the help in advance.

~Will

---

### Post by incubus on 2006-03-09
Dear Will,

When you try to load a page, does it spend a long time on "looking up <some name>"?

In my case my primary DNS server has been very slow, so I manually edit the file
/etc/resolv.conf

and comment out the first server IP address (inserting # before it). After that the connection flies again.

incubus

PS: the other way to test this is to ping an IP address as opposed to a name. Try to ping 66.102.7.104. Is it slow as well?

---

### Post by sublime on 2006-03-09
awesome.  ive also been having this same issue for liek a week and this fixed it.  thanks a lot

---

### Post by incubus on 2006-03-09
sublime,

Funny, we're in the same city. We can blame on Cox, can't we? :) 

incubus

---

### Post by sublime on 2006-03-09
lol yes.  i say down with the 68.2.16.245 server.  destroys my connection speed.

---

### Post by Offthedeepend on 2006-03-09
Hi,
I'm having a similar problem with slow connection speed.  I'm a first time Linux user with Ubuntu 5.10 just installed on a Dell i9300 laptop (dual boot with WinXP).  My ADSL connection is reasonably fast, and browsing the internet with firefox is fine, pages load quick, but I'm currently trying to use the 'Automatix' script for installing various extra applications.  The script seems to be working fine, but is downloading files extremely slowly, mostly less than 5kb/s.  It has taken several hours just to get a third way through the list.  

I have had to cancel Automatix and restart, which seems to be fine (?), but at this rate it will take days to finish!  I'm a complete beginner with Linux so am not sure whether I need to adjust some configuration settings or something else.  I am using a belkin router (connected through cable - haven't figured out the wireless yet...) so could be something to do with that?

Apologies in advance if I should have posted this problem in a separate thread, but it seemed similar to the original post, so I though I'd start here first.  

Appreciate any advice you might have.

---

### Post by incubus on 2006-03-11
I'm sorry I can't offer much help, as I never used the Automatix script and I'm ignorant about its functioning.

Is the problem limited only to Automatix downloads? Does it happen to all Automatix downloads?

If I'd have to take a guess, it could be that a specific server is being overwhelmed by people requesting downloads. In this case it wouldn't be a problem with automatix or ubuntu or your computer at all.

incubus

PS: By the way, welcome and don't be ashamed to ask that in the Automatix thread. I'm sure they will be glad to help you out as well.

---

### Post by Offthedeepend on 2006-03-12
Thanks, yeah I suspect it may be server overload also.  Doesn't seem to happend with all Automatix downloads, just some - mainly the larger files.  I will wander over to the Automatix threads and see what I can find. 

Cheers,

---

