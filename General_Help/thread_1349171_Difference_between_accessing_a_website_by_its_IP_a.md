---
title: "Difference between accessing a website by its IP address and by its domain name?"
date: 2009-12-08
forum: General Help
---

### Post by emigrant on 2009-12-08
hi all?
what is the difference between the two methods other than difficult to remember the ip?
i mean security wise.

eg:
canonical.com
91.189.94.12

thank you very much.
:popcorn:

---

### Post by VastOne on 2009-12-08
One relies on DNS, the other (IP) hits it directly

---

### Post by emigrant on 2009-12-08
that means the ISP doenst know what site the user visits?

---

### Post by VastOne on 2009-12-08
> **emigrant said:**
> that means the ISP doenst know what site the user visits?

The ISP will always know....

---

### Post by emigrant on 2009-12-08
so the only benifit is easy to remember? :mad:

---

### Post by VastOne on 2009-12-08
> **emigrant said:**
> so the only benifit is easy to remember? :mad:

Yes and no...By going directly IP you could get there faster bypassing DNS servers...Depends on where you are going....

---

### Post by lykwydchykyn on 2009-12-08
> **emigrant said:**
> so the only benifit is easy to remember? :mad:

The same server, using a single IP address, can host multiple sites with different names.  This is called virtual hosting.

Conversely, a single DNS name can resolve to multiple IP addresses, for purposes of load-balancing (e.g., try pinging [www.google.com](www.google.com) 3-4 times in a row, and see that it comes up with different IP addresses each time).

So, mostly it's about easy-to-remember, but there are other advantages.

---

### Post by smcleish on 2009-12-08
> **emigrant said:**
> so the only benifit is easy to remember? :mad:

There may also be differences, including security differences, based on the configuration of the web server at the other end. For example, if the web server uses a certificate, [https://sitename.com](https://sitename.com) will not throw up an error message, but [https://ipaddress](https://ipaddress) will, because the certificate name will only match sitename.com. The web server is also quite likely not to listen for requests for [https://ipaddress](https://ipaddress) (on apache, you'd need to deliberately configure this for it to happen, I think) so you might get a 404 not found error.

The browsing experience might also be rather different. I haven't tested this, but I suspect that accessing via IP address will not pass cookies back that came from the web server by site name. Another potential issue which I haven't tested is that using IP addresses might bypass certain kinds of load balancing, which would reduce the speed of access to high usage web sites.

On the other hand, if your ISP's DNS service is flaky, you might get more reliable access through the IP address - I remember, back in the mid 90s, that I knew by heart the IP addresses of some of the sites I used frequently - Lycos and Yahoo, for example (this was before Google, and even before Altavista), because I needed them to reliably access the web sites.

---

