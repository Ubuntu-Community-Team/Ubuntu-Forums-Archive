---
title: "Rtorrent can't download at full speed, but other programs can"
date: 2009-06-30
forum: General Help
---

### Post by tripsich on 2009-06-30
Hi all,

Got a bit of a dilemma here I hope you can help me with. Ive got an old laptop (p2, 128mb) that I want to re-purpose as a bittorrent machine. Thus, I've decided to go with rtorrent.

I installed it fine, configured the .rtorrent.rc file and tested it out on a torrent.... only to get terrible speeds. It connected to about 40 peers (out of ~300) but could only manage to get a dl speed of about 1.5 kilobytes.

Just to make sure, I immediately tested the same torrent file on Deluge, then Transmission and finally uTorrent (on my Windows machine). Each time I could max out my connection. 

I'm not sure what the problem is. I then tried rtorrent with it's default settings, but that didn't change anything. The conf file is as below:

```

max_peers = 40
max_peers_seed = 20
download_rate = 0
upload_rate = 15
session = ./session
port_range = 6790-60000
port_random = yes
check_hash = yes
use_udp_trackers = yes
 encryption = allow_incoming,enable_retry,prefer_plaintext
dht = auto
 dht_port = 6881
peer_exchange = yes

```As a comparison, my Deluge settings are as follows:
use random ports (incoming and outgoing)
encryption is turned on
upnp, nat-pmp, peer exchange and dht are turned on

Transmission was using its default settings:
upnp/nat-pmp turned on
listening port 51413
use peer exchange

I then went and tested about 20 other torrents (all with high numbers of seeders, and using different trackers), but to no avail.

Has anyone experienced a similar problem before with rtorrent? Any help in resolving this issue would be greatly appreciated.

---

### Post by lovinglinux on 2009-06-30
Why don't you use Deluge instead? You can max out with it and it has remote gtk, webui and cli interfaces, if that's what you are looking for on rtorrent.

---

### Post by tripsich on 2009-06-30
Because it's now turned into a case of "why the heck wont rtorrent work properly" and it's going to bug me to no end now, lol :)

---

### Post by lovinglinux on 2009-06-30
> **tripsich said:**
> Because it's now turned into a case of "why the heck wont rtorrent work properly" and it's going to bug me to no end now, lol :)

That's true :)

---

### Post by tripsich on 2009-07-01
Been doing more tests, and I think I know what the problem is.

I don't have a dsl router, instead my internet breakout is further further up the network stream (my lan connects to a larger lan and then a wan). When I tested rtorrent onto a friend's machine (who has a standard dsl router + lan setup in his home), rtorrent worked perfectly.

It looks like rtorrent doesn't like multiple natting, possibly because it doesnt support nat-pmp. I'll try doing some port-forwarding to see if that works

---

