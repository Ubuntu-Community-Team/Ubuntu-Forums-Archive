---
title: "Start application on successful internet connection"
date: 2010-11-01
forum: General Help
---

### Post by c0ldfusi0n on 2010-11-01
Hi guys.

I'm using 10.10x64 and I had the idea to configure which applications should start at boot. The "Startup Applications" app is useful, but it's pretty standard in terms of options.

I'd like to be able to start some applications not on GNOME-load, but on successful connection to a wireless network - stuff like TweetDeck and Pidgin.

Any advice?

---

### Post by blueridgedog on 2010-11-01
Scripts to run applications after the network is up can be placed in /etc/network/if-up.d/

See:

[https://wiki.ubuntu.com/OnNetworkConnectionRunScript](https://wiki.ubuntu.com/OnNetworkConnectionRunScript)

---

