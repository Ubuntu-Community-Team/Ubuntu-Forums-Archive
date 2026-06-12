---
title: "Tor along with Deluge and Chromium"
date: 2010-01-15
forum: General Help
---

### Post by sindhu_sundar on 2010-01-15
Hi!

I am user or Tor (Onion router for privacy).

I use Chromium browser for web browsing and I use Deluge to download via torrents.

My problem is that there is no Gnome applet to switch between "locations" of network proxy settings in Gnome, on the fly. Due to which I have to manually change the settings every time I want to use my torrent client, because Google chrome doesn't have an individual option of using SOCKS proxy - it uses Gnome environment proxy settings. 

I am forced to use Firefox with tor button while keeping my gnome proxy settings as "direct connection to the internet".

I want to be able to use Tor via Google Chrome but at the same time use my torrent client via direct connection to the internet.

How can I go about?

---

### Post by marshmallow1304 on 2010-01-15
You may wish to try [tsocks]("apt://tsocks").


> transparent network access through a SOCKS 4 or 5 proxy

tsocks provides transparent network access through a SOCKS version 4
or 5 proxy (usually on a firewall). tsocks intercepts the calls
applications make to establish TCP connections and transparently
proxies them as necessary. This allows existing applications to use
SOCKS without recompilation or modification.

---

### Post by xthatrox on 2010-07-17
Try using switchy - it works great and has plenty of extra features.  Version 1.6 works well on ubuntu.  

[https://chrome.google.com/extensions/detail/caehdcpeofiiigpdhbabniblemipncjj](https://chrome.google.com/extensions/detail/caehdcpeofiiigpdhbabniblemipncjj)

---

### Post by MithrandirAgain on 2010-07-23
> **xthatrox said:**
> Try using switchy - it works great and has plenty of extra features.  Version 1.6 works well on ubuntu.  

[https://chrome.google.com/extensions/detail/caehdcpeofiiigpdhbabniblemipncjj](https://chrome.google.com/extensions/detail/caehdcpeofiiigpdhbabniblemipncjj)

Thanks for posting that link! It works great on Iron too! :KS

---

### Post by ewan86 on 2010-08-18
When I installed it in chrome it said it needed to access to all web sites i visit and all the data on my computer?? Should I be concerned about my privacy!!???

ps and if not what settings do I put in?? I have Tor installed and working on firefox with the tor button.

---

### Post by magnatron on 2010-11-21
Chrome has an app for that called Proxy Switchy  [http://switchy.samabox.com/](http://switchy.samabox.com/)  All these Tor or Onion route settings onto Deluge are a bit over-kill imho as deluge encrypts all your traffic to and from the peer anyways, so they know your downloading, they just have no idea what. In the Deluge settings there is an option to import a blocklist of IP ranges. HTH

---

