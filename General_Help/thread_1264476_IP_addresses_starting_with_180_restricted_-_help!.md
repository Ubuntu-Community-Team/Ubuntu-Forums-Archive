---
title: "IP addresses starting with 180 restricted - help!"
date: 2009-09-12
forum: General Help
---

### Post by mnoyes on 2009-09-12
Can't load some websites. Asked ISP for help, was told that the sites I had first noticed the problem with -- [www.nytimes.com](www.nytimes.com) and [www.ila1588.org](www.ila1588.org) -- were fine but that the ISP had been assigned IP numbers starting with 180 as a global IP by APNIC and that many sites have access restrictions on IPs beginning with 180.

The IP for my machine starts with 192...

Help! Any ideas for how I can get around this? The ISP says they are contacting the providers who are blocking access but have had no luck so far. What can I do? Can I set up a different IP for my router somehow? 

FWIW I tried TOR -- which works, but is very slow (understandably, given its tech)...

What other options do I have?:confused:

---

### Post by grizzler on 2009-09-12
> What other options do I have?

Not a lot, I'm afraid. This looks like a bogon filtering problem. See [http://en.wikipedia.org/wiki/Bogon_filtering](http://en.wikipedia.org/wiki/Bogon_filtering)

The IP for your machine starting with 192 (192.168. most likely) has nothing to do with it. That's just the LAN side of the router. Your ISP will have to deal with it and keep contacting site admins who don't update their bogon filters properly.

---

### Post by mnoyes on 2009-09-12
Thanks! 

It seems that APNIC allocated 180 addresses to OCN (a major Japanese ISP) but some (many?) sites still have this address listed as a Bogon...

So, I have to wait until some admin changes the filters? I guess I will just do what I can to pressure the ISP...

Ironic that the bogon filter itself becomes bogus.

UPDATE: I managed to reset the IP address and all is fine.

---

