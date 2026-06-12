---
title: "Bit Torrent ports +firewalls"
date: 2009-11-26
forum: General Help
---

### Post by jessiebrownjr on 2009-11-26
Hey guys, was curious... I was reading that ISP can limit the speeds or close ports commonly used for bit torrent. I can get up to 700 KBS, but as of late, i only get 100-200. This is odd considering I have files that have up to 200 seeders sometimes. Now my question has a few sides. I know how I can change the port manually in the tranmission program, but it has the checkbox of "Use UPnP or NAT-PMP port forwarding from my router." I have it checked. 

I guess im fuzzy on what the port forwarding does. Could I uncheck it, open a port in my firewall, and move transmission to that port? I tried that with GUFW and it seemed to say the port was still closed. Any help would be appreciated!

---

### Post by emachnic on 2009-11-26
If you're using a router, you have to log into it from you browser and set up port forwarding to forward the traffic to the port specified in your BT program. There are a lot of articles about this online.

---

### Post by bodhi.zazen on 2009-11-26
In a nut shell ...

Your router acts as a firewall. Port forwarding opens a route through your firewall.

By default, Ubuntu has a permissive firewall so you probably do not need to open a port in Ubuntu.

Torrents are more complicated because yes, ISP do sometimes block the default torrent ports. Because of this, each client uses a different port. You will need to look up your default ports.

In general, opening a port for torrents does not affect your download speed, but people are able to upload from you faster (as by default neither your router nor ubuntu should limit download speed).

For Ubuntu I posted some blogs :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

Beyond those basics I suggest you may wish to do some reading on firewalls and torrents. The subject is complex, but well documented on a number of sites, so if you have a specific question post back.

---

### Post by lovinglinux on 2009-11-26
> **jessiebrownjr said:**
> I guess im fuzzy on what the port forwarding does. Could I uncheck it, open a port in my firewall, and move transmission to that port? I tried that with GUFW and it seemed to say the port was still closed. Any help would be appreciated!

The UPnP feature automatically opens the required port in your router, not in the firewall. If you uncheck UPnP, you will need to open the port manually on your router, otherwise the number of connected peers will be reduced, since incoming connection requests won't reach your BitTorrent client, even if the port is open in the firewall. Nevertheless, opening the port on the firewall is still required, no matter if you use UPnP or not. This must be done manually, since UPnP does not interact with the firewall.

> **bodhi.zazen said:**
> In general, opening a port for torrents does not affect your download speed, but people are able to upload from you faster (as by default neither your router nor ubuntu should limit download speed).

Opening a port for torrents only allows other peers to request connections to you. This is not directly related to download speed, although it will indirectly improve it, due to increased number of established connections with different peers. 

Here is a quote form my [BitTorrent guide](http://ubuntuforums.org/showthread.php?t=1259923), explaining the effect of a closed port:

> **lovinglinux said:**
> [color=#CC0000][SIZE="3"]Closed Port[/SIZE][/color]

The first thing most users suggest when questioned about connection issues is that the torrent [port](http://en.wikipedia.org/wiki/Computer_port_%28software%29) is not properly configured in the client or it is closed by the router/firewall. While a closed port will usually result in lower download speeds, it doesn't prevent you from connecting to some peers, downloading and uploading. Nevertheless is not recommended and impolite to join a swarm with closed ports.

The port configured in the BitTorrent client is used only for incoming **[COLOR="DarkRed"]unrequested[/COLOR]** connections. So even if it is closed, your client will still be able to request connections to other peers, but won't get any requests from them. Once the connection is established by your request, the data transfer between your client and the connected peer is always allowed. This means a closed port only reduces the number of connected peers. This happens because each peer has a limited number of possible simultaneous connections, so they will not accept your connection requests all the time, but they might try to connect to you when they have a connection slot available. So, having the port opened and properly configured will increase the number of connected peers.

Please notice that the number of connected peers does not means that they will all be uploading to you at the same time. Your client connects to a large amount of peers and keep sending them requests for content pieces. The peer being requested might not have a free upload slot at the time of request, so the client tries another connected peer. So as general rule, the more peers you can connect, bigger will be your chances of getting more file pieces at the same time and thus your download speed will be higher. 

That guide explains everything you want to know. It also has a troubleshooting section.

---

### Post by jessiebrownjr on 2009-11-27
> **lovinglinux said:**
> The UPnP feature automatically opens the required port in your router, not in the firewall. If you uncheck UPnP, you will need to open the port manually on your router, otherwise the number of connected peers will be reduced, since incoming connection requests won't reach your BitTorrent client, even if the port is open in the firewall. Nevertheless, opening the port on the firewall is still required, no matter if you use UPnP or not. This must be done manually, since UPnP does not interact with the firewall.



Opening a port for torrents only allows other peers to request connections to you. This is not directly related to download speed, although it will indirectly improve it, due to increased number of established connections with different peers. 

Here is a quote form my [BitTorrent guide]("http://ubuntuforums.org/showthread.php?t=1259923"), explaining the effect of a closed port:



That guide explains everything you want to know. It also has a troubleshooting section.

Alrighty, I enabled the port I wished to use through my firewall+ router. as said above it doesn't seem to directly make a drastic download speed improvement. 

I have upnp *checked* with my firewall/router having the new port assigned and it shows the port as open. With upnp checked, firewall allowing, and router disallowing, it shows it to be closed... this is as expected right? 

Also a question thats partially related.. I rebooted into windows to play some quake 3 and bam, my windows firewall said I got... 24 attempted connections to my new opened router port and it blocked them all..  I don't have a static IP, but it seems to end up the same every time... my ip always ends in 102 on the home network, so those guys were possibly torrent clients trying to reconnect to my torrent i hope? If not I feel like it was a big problem. I just put 2+2 together as I was typing this and realized it was hopefully the torrent cause I had just rebooted from linux+transmission.

On my router, I made the port only open for TCP.. Is this better then "both" or does it matter?

Thanks guys for your help, definately making this less confusing. I will read all the guides you suggested guys, thanks again!

---

### Post by lovinglinux on 2009-11-27
> **jessiebrownjr said:**
> I have upnp *checked* with my firewall/router having the new port assigned and it shows the port as open. With upnp checked, firewall allowing, and router disallowing, it shows it to be closed... this is as expected right? 

Yes, if you disable UPnP on the router or in the client and don't manually forward the port, then it will show as closed. 

**> **jessiebrownjr said:**
> Also a question thats partially related.. I rebooted into windows to play some quake 3 and bam, my windows firewall said I got... 24 attempted connections to my new opened router port and it blocked them all..  I don't have a static IP, but it seems to end up the same every time... my ip always ends in 102 on the home network, so those guys were possibly torrent clients trying to reconnect to my torrent i hope? If not I feel like it was a big problem. I just put 2+2 together as I was typing this and realized it was hopefully the torrent cause I had just rebooted from linux+transmission**

You are correct. Those are ghost packets from peers trying to connect to your BitTorrent client. It takes some time to update the tracker info and the list of peers everybody gets from it. So until then, they will try to connect to you, even if you turn the computer off.

> **jessiebrownjr said:**
> On my router, I made the port only open for TCP.. Is this better then "both" or does it matter?

You need tcp for the regular port and udp for the DHT port. Since regular torrent download and DHT uses different ports, you don't have to enable both for each. Keep in mind that if you are using UPnP, you don't have to manually open the ports on the router. UPnP does that for you, automatically.

---

### Post by jessiebrownjr on 2009-11-27
I turned off upnp and set it to my custom port, and I opened that custom port up in GUFW + my router. Now you said *FORWARD*, but I don't have it forwarded( atleast as far as my understanding goes I dont).

When I get back home ill take a glance back at the router and see if I can make heads or tails of it.

---

### Post by lovinglinux on 2009-11-28
> **jessiebrownjr said:**
> I turned off upnp and set it to my custom port, and I opened that custom port up in GUFW + my router. Now you said *FORWARD*, but I don't have it forwarded( atleast as far as my understanding goes I dont).

When I get back home ill take a glance back at the router and see if I can make heads or tails of it.

When I say FORWARD is the same as opening the port in the router, because you forward all incoming connections on the selected port to the internal IP of your machine.

---

