---
title: "Is there a way to have 2 instances of the same app but using different ports?"
date: 2010-08-01
forum: General Help
---

### Post by em3raldxiii on 2010-08-01
First of all, this is mostly a curiosity ... but I may have a use for it one day LOL.

So let's say I have an application that uses net traffic (TCP or UDP, I don't think it matters) both on an incoming and outgoing basis.  This application wants to use port 12345 for it's communication.

Now, is it possible to run 2 instances of this application simultaneously, only reroute the traffic for one of the applications away from 12345 to 13456 (or any other random port number)?  I guess it would be a little bit like port-forwarding.

I know I could do this if I had 2 machines connected to the same network, each running a copy of the application.  The router would port-forward 12345 communication to one machine (lets say 192.168.0.100:12345) and then I could have it port-forward 13456 to the other machine  (lets say 192.168.0.101:12345).  But in this case, the application is still only listening on 12345 for each machine; the router handles the rest.

But what if I didn't have 2 computers on my network, and I still wanted to run two instances of the same app?  Can I have something intercede and like ... create a virtual port for specific applications?

---

### Post by em3raldxiii on 2010-09-03
bump

---

### Post by Rubi1200 on 2010-09-03
What app. are we talking about here? A web browser, torrent client? I think you need to be more explicit about what exactly you want to achieve in order for someone to suggest some possible solutions.

---

