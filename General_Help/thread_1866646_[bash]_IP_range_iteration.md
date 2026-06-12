---
title: "[bash] IP range iteration"
date: 2011-10-21
forum: General Help
---

### Post by xqwzts on 2011-10-21
Hi

I need to write a script that would iterate through all IP addresses in the given range (all octets may be different). Is there any realtively simple way of doing this, or I will have to write a big muddle of if's and for loops? If there is, I will be very  grateful for any clues.

---

### Post by AlphaLexman on 2011-10-21
So, you want **ALL** IPv4 iterations 256^4 = 4,294,967,296 (almost 4.3 Billion) options.

Unless you include IPv6, which is 256^6 iterations = 281,474,976,710,656 (about 281.5 Quadrillion) options.

Of course the above examples are extreme...

What are the ranges you are looking for?

---

### Post by xqwzts on 2011-10-21
I need it for an university project - the scripts gets 2 IPv4 addresses as arguments and checks some ports using netcat for all of the addreses in the range. It's just for testing so I don't think it will be used to iterate all 4 billion addresses, however I don't have any ranges given, so I guess it's supposed to work correctly for any of them.

---

