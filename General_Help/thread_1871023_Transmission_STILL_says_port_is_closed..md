---
title: "Transmission STILL says port is closed."
date: 2011-10-28
forum: General Help
---

### Post by XEtedBear on 2011-10-28
I've followed that excellent Tutuorial on Bit Torrent Optimisation and Trouble Shooting. I even understood some of it.

My port for incoming connections in Transmission remains stubbornly closed and download of a file has stalled about 75% of the way through for the last 12 hours. Here is what I have done (without achieving any progress):

1. Set router port forwarding for this identified port as well as for UDP on port 1900
2. Created a rule in UFW to allow in/out from/to anyhwere on this port, as well as on my loopback IP address
3. Allowed incoming UDP from anywhere on port 1900
4. Enabled full logging in ufw
5. Changed the incoming port in Transmission to a quite different number and added rules accordingly in both router and firewall
6. Attempted to see myself via the service on 'Canyouseeme.org'
7. Checked 'Use UPnP or NAT-PMP port forwarding' option in Transmission

Number of connected peers ranges from 11 to 30+

At all times Transmission reports the relevant port as being closed

I cannot see myself

There are no relevant entries in ufw log

There is no download activity

Do I conclude that VirginMedia have closed all ports?

---

### Post by satanselbow on 2011-10-28
port 1900 is a listed / known service port so should be avoided for other purposes.


I would try something in the much higher range 50000+ As they are largely "free" and unlikely to be "monitored" for such traffic.

The default bittorrent ports 6881 etc should be avoided ;)

---

### Post by t0p on 2011-10-28
I'm not saying that your ISP *is* responsible; but many ISPs *do* have traffic management policies that slow down or even completely disallow p2p services.

Try using a VPN or another proxy server setup.

---

### Post by satanselbow on 2011-10-28
VM do use bandwidth shaping but afaik as a user they do not block higher end ports ;)

---

### Post by XEtedBear on 2011-10-28
> **satanselbow said:**
> 


I would try something in the much higher range 50000+ As they are largely "free" and unlikely to be "monitored" for such traffic.

Th

And that's exactly what I did. But still no progress.

---

### Post by XEtedBear on 2011-10-28
> **t0p said:**
> I'm not saying that your ISP *is* responsible; but many ISPs *do* have traffic management policies that slow down or even completely disallow p2p services.

Try using a VPN or another proxy server setup.

But this would not explain how I was able to receive 2.1 GB out of 2.9 GB of the torrent BEFORE realising that things like ports existed!

As far as using VPN or another proxy server is concerned, I don't have clue. The only type of proxy server I know is the rather over-fed, badly educated, distinctly un-bathed type who appears at your door and hands you  a grubby piece of paper from some unprincipled shark elsewhere. VPN sounds like  medical procedure to me - but that can't be what I'm doing wrong, surely?

---

### Post by XEtedBear on 2011-10-28
> **satanselbow said:**
> VM do use bandwidth shaping but afaik as a user they do not block higher end ports ;)

I have tried a wide range of ports about 55000. canyouseeme open port check tool times out on every one, even with port forwarding set to a wide range.

Surely VM can't block all these legitimately?  I suspect there has to be some other reason.

---

### Post by satanselbow on 2011-10-28
How exactly have you set the port forwarding up on your router?

You should have a screen in your (router) control panel that allows you to enter a manual port range (you only need one port) so set it up as eg 50505 - 50505 and then enter you internal ip ie 192.168.0.100

That is all you need at the router end. Some routers require a reboot before the forwarding will become active ;)

In your torrent client set the "port used for incoming connections" to the same port (50505) and put a tick in the use "use upnp from router". You will also want to uncheck any box that says "use random port" as that would undo your good work on next restart.

As for UFW... never had the need - so can't help sorry :(

---

### Post by XEtedBear on 2011-10-28
> **satanselbow said:**
> VM do use bandwidth shaping but afaik as a user they do not block higher end ports ;)


And another thing: I'm now 'happily downloading 4.5 GB of the Beijing Olympics opening ceremony (a random torrent selection) from 1 of 9 connected peers at a very respectable rate on a CLOSED Transmission port.

Shows how much I know.

But no luck on the file I really want, which makes me think that it is the file that is being blocked rather then the port. 

I suppose that's what you get from trying to look at dirty software. I'm disgusted (but not of or by Tonbridge Wells) to think I'm trying to download something with the word 'OEM' in the title. Uggh!

---

### Post by XEtedBear on 2011-10-28
> **satanselbow said:**
> How exactly have you set the port forwarding up on your router?

Some routers require a reboot before the forwarding will become active ;)
(

Now he tells me....

But damned good thinking, that man. Have the rest of the morning off.

Yeah, I did set the port forwarding in the way you suggest.

---

### Post by XEtedBear on 2011-10-28
I have 1 explanation for the failure to download:

Whilst not knowing the difference between a seed, a leer and a peach I have found that the file I am trying to download has no seeds. 

But that doesn't explain the key issue: why does Torrent see the port as closed when ufw status shows 'allowed' and why can't the Open Port Check get a positive response?

---

