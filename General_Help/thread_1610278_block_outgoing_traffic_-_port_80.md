---
title: "block outgoing traffic - port 80"
date: 2010-10-31
forum: General Help
---

### Post by Monotoko on 2010-10-31
Hi there,

I am writing an article on how to block certain sites using Ubuntu. I have successfully set up squid3 to use port 8080 and told it to use a file which contains the blocked sites.

I can then set .bashrc and the browsers to use the proxy. However, they can easily switch it back to "direct connection" and bypass squid. How do I stop this?

I assume I need to block outgoing traffic on port 80 using iptables? How do I do that? (I have never been so good with iptables)

~Monotoko

---

