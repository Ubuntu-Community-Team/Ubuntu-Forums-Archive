---
title: "Adding routes to dynamic pppoe connection?"
date: 2011-07-22
forum: General Help
---

### Post by SawyerX on 2011-07-22
Is it possible to add the routes to my routing table for dynamic pppoe connections? I have this setup on windows 7 with power-shell scripting and some 3rd party commercial pppoe client called Cfos, but since I'm  now trying to move away from windows to Ubuntu and cant use the same programs anymore and its getting abit tricky now.

I'm not trying to do any fancy load balancing here just some basic stuff which should be possible.

Here is same basic info.

My ISP resets my pppoe connection every 24 hours. However the advantage of this is that I can call out 2 or more simultaneous PPPOE connections through the same modem.

This is my routing table I wrote which has 5 PPPOE connections [http://dl.dropbox.com/u/4531531/Siol/ppp.txt](http://dl.dropbox.com/u/4531531/Siol/ppp.txt)

Id like this to be automated when the PPPoes reconnect and the computer restarts.

:popcorn:

---

### Post by SawyerX on 2011-07-22
I did try that as per one example I found but still no joy.

[http://dl.dropbox.com/u/4531531/Siol/rc.local](http://dl.dropbox.com/u/4531531/Siol/rc.local)

---

### Post by SawyerX on 2011-07-22
All right. I found the right folder to be the ip-up.d for the script. But now my problem is that the script seems to execute to fast because only ppp0 and if lucky ppp1 routes are added.
I guess I need a delay in it. How to do that?


EDIT:
all right solved that to.

thank for you help guys.

---

