---
title: "Block Facebook Chat in IM clients"
date: 2010-11-19
forum: General Help
---

### Post by CrusaderAD on 2010-11-19
I have Facebook blocked in certain areas on my network. So certain machines cannot navigate Facebook. One other issue is chatting with 3rd party clients. How do I block that? Can I block a certain port on the firewall/router? I can't seem to find what Facebook uses.

---

### Post by tosk on 2010-11-19
How are you blocking Facebook in the browser? Using a proxy?

If you're blocking all connections to *.facebook.com from iptables, it should block Facebook Chat.

Facebook Chat operates over the XMPP protocol. It operates normally on port 5222. Blocking that port should disallow communication with XMPP chat server.

If you want to allow XMPP traffic, but not Facebook Chat, then block all communication with chat.facebook.com and leave 5222 open.

---

