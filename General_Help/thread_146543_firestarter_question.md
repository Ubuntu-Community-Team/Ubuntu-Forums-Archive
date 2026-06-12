---
title: "firestarter question"
date: 2006-03-18
forum: General Help
---

### Post by Stem on 2006-03-18
I have firestarter up and running and in terminal it says it is running, but when I go to "shields up" and run a test all my ports fail except for 4, I am also connected thru a router. The main firstarter screen shows no blocks of pings or anything else.

---

### Post by Zelut on 2006-03-18
How is your router setup?  Are you forwarding a lot of ports to your machine?  If you have 0 port forwarding setup & you set it to 'ignore ping request' you should pass a few more tests.

what ports are failing? are these also forwarded?

---

### Post by Stem on 2006-03-18
I am not forwarding any ports on the router, and the do not allow ping is checked as well which should stop that port but it fails that part of the test anyway.The router is set up in the default mode for any of those settings

---

### Post by powder on 2006-03-18
You should call tech support for your router.  If you're not forwarding any ports then your router should be stealthing all of the ports that "Sheilds Up" tests.

---

### Post by Stem on 2006-03-18
ok, thanks, I thought it did not make sense, I will try that

---

### Post by Stem on 2006-03-18
Ok, I have a linksys wrt54g router and got the open source firmware and upgraded to that. Still my ports fail the test. 
I am wondering if it has something to do with the fact that I use a high speed satellite connection? I get no blocked events on Firestarter and under active connections I get a weird 127.0.0.1 on port 631. 
Any thoughts ! 

Could it be that satellite connections respond to requests on its modem?

---

### Post by Zelut on 2006-03-19
127.0.0.1 (yourself) and port 631 (printing) should be fine.  I wouldn't worry about those.  You can find more info on 631 and its details with a quick google search for 'port 631'.

I don't know enough about the difference between landline & satellite connections to tell you if that would be the issue.

---

### Post by 5-HT on 2006-03-19
Since you're going through a router, the IP you're testing will not be the private one assigned to the PC but the router's WAN IP (if there's no fowarding going on).

Is the PC in the router's DMZ by any chance? Except for a few (usually just one) exception, all ports should appear either closed or stealthed if the router's doing its job.

That only 4 ports were closed suggests to me that your ISP is probably blocking them, and that the router may not be configured properly.
There should be a nice configuration wizard in the router's web interface.

---

### Post by OffHand on 2006-03-19
If you use Peerguardian it will un-stealth Firestarter too.
But if you got a router with firewall Firestarter is kinda useless.

---

