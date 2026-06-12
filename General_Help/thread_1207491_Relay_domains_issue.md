---
title: "Relay_domains issue"
date: 2009-07-08
forum: General Help
---

### Post by craigjw on 2009-07-08
Hi All,

I have the following in my main.cf file:


relay_domains = hash:/etc/postfix/relay_domains
relay_recipient_maps = hash:/etc/postfix/relay_recipients

If I try to send to a recipient on a domain listed in the relay_recipients it delivers, if I try to send to one on the same domain who isnt listed in relay_recipients it fails. If I try to send to someone on a domain not listed in relay_domains it goes through.

Anyone shed any light on how it works?

Thanks,
Craig

---

