---
title: "How can I enable irssi's proxy?"
date: 2012-05-31
forum: General Help
---

### Post by SavvasKatseas on 2012-05-31
I've recently installed **irssi**, **irssi-dev** and **irssi-scripts** on an Ubuntu Server. I intend to use irssi as an IRC proxy. After following the instructions which I found on various pages, irssi doesn't seem to act as a proxy. The instructions were:

[LIST]
[*]/LOAD proxy
[*]/SET irssiproxy_password password
[*]/SET irssiproxy_ports network=port
[/LIST]

I've also set up a network and one server in it.

When trying to connect to the proxy I get

**Unable to connect to remote host: Connection refused**

I'm getting the same message if I try to **telnet 127.0.0.1 8888**, 8888 being the port I specified for the network I created in irssi's proxy.

---

