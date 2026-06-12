---
title: "Setting up a Samsung ML-02851ND printer"
date: 2010-06-14
forum: General Help
---

### Post by DannyJohansson on 2010-06-14
hello all,

Perhaps I am going about this all wrong.  I run a couple Ubuntu machines in the house, my wife runs XP, there's an eee, etc.

So I got a Samsung ML-02851ND printer thinking that I could just plug it into my router and then install the printer on all of the various machines and I could print from them.  I guess I realize that I can hook up the printer to a host machine and go that route, but i thought the whole point was to hook the printer up to the router.

deal or no deal?  thanks for any and all help...

---

### Post by DannyJohansson on 2010-06-15
OK, I figured this out with the help of one of my network guys at work.  I assume this advice is true most all networkable printers.

The trick is that you have to make the IP address of the printer be a static address, not DHCP.  Once I logged into my router and forced the printer to have a static IP, ubuntu installed the driver and printed a test page very quickly.  I then went to the wireless ubuntu box and got it printing, and then to my wife's XP laptop and got it printing too.

It's a simple tweak, but apparently makes all the difference in the world.

---

