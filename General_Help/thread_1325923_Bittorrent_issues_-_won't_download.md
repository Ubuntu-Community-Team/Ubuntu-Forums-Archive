---
title: "Bittorrent issues - won't download"
date: 2009-11-13
forum: General Help
---

### Post by zookrider on 2009-11-13
I'm a new bittorrent user and I'm Having a horrible time trying to get it to work. I'm trying to download a file using Transmission. I first found the file I needed, downloaded the torrent and opened it in Transmission. I watched as the status on my torrent varied between
> Downloading from 0 of 1 connected peers, idle
and 
> Downloading from 0 of 60 connected peers, idle
Note that I had chosen the file with the most seeders available, point being that I wasn't actually getting any data. I figured out that I needed to open my ports, but I'm not sure which. I checked Transmission's properties and found two:
Under the Network tab, Incoming Peers - 51413
Under the Web tab, Listening Port - 9091
I tried to open both ports using the following commands:
> sudo ufw allow 9091
sudo ufw allow 51413
Each of which resulted in:
> Skipping adding existing rule
And:
> sudo iptables -A INPUT -p tcp --dport 9091 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 51413 -j ACCEPT
Which didn't give me any feedback at all.
I also turned off Firestarter, a Firewall I have installed on my computer.
After executing these commands I went back to the Network tab where Transmission tested port 51413 and dutifully told me that it is still closed. Additionally, now my torrent status reads:
> Downloading from 0 of 0 online peers, idle
Progress? I think not.  This status hasn't changed in 12+ hours. I tried deleting that torrent and finding another, same result. I'm pretty well stuck. Please help.

Specifics:
Juanty
Toshiba Satellite
Transmission 1.51
Firestarter 1.0.3

---

### Post by unamanic on 2009-11-13
Is there a router between your computer and your modem?  If so you need to enable port forwarding on your router.

---

### Post by ed-koala on 2009-11-13
Stopping the firewall was a good step.  Have you forwarded ports from your router to your PC?  I personally have never done that via code from Ubuntu, I use my web browser and go to the IP address of the router, and configure there.  A web search of port forwarding should get you specific instructions on how to set up your router brand.

Next step.  Transmission works, but I've never liked it.  It's not your problem, but you may want to install and try Deluge.  Easy to config and use.  Just a suggestion.

The torrent ... how "popular" is it?  Try one from a torrent site that lists LOTS of seeders and a small number of peers, if that doesn't go well, then it's not the torrent.

Settings ... no matter what program you use, if you set your upload bandwidth too high, you'll throttle your torrent.  You'll need to know your upload/download internet speeds to get your bandwidth settings optimal.

So, no firewall, forwarded ports, and proper bandwidth = nice torrents. If you're worried about the firewall not being up ... you run Ubuntu, don't sweat it.

If you need help with any of this, just say which one and give info like router brand/model (for port forwarding), or program and up/down internet speeds (for your bandwidth settings).

---

### Post by zookrider on 2009-11-13
Router fowarding is probably my issue. I am in an environment where internet is being disseminated by a central router over which I have no control. Am I just screwed?

---

### Post by bashphoenux on 2009-11-13
kinda  yes :)

---

### Post by lovinglinux on 2009-11-13
First you shouldn't be using Firestarter and UFW at the same time. Most likely that you have conflicting firewall rules because if this.

So first I recommend removing Firestarter and installing gufw, which is a graphical interface for UFW. To make sure you don't have conflicting rules, follow the steps below:

Close Firestarter, if it is already opened, then open a terminal and run this:

```
sudo apt-get purge firestarter
```

This will completely remove firestarter. Then run the following commands:

```
sudo ufw disable
sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
```

This will disable ufw and cleanup any firewall rules, allowing all traffic.

Then install gufw:

```
sudo apt-get install gufw
```

To start gufw go to "System >> Administration >> Firewall Configuration". You can enable it from there and create the rules to open the BitTorrent ports. Nevertheless, I recommend that you leave it disable until you properly configure your BitTorrent client, so you can determine if the problem is somewhere else.

In regard to opening ports in the router and the firewall, it doesn't prevent you from downloading torrents. Instead of explaining why here, please see my tutorial [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923). It has everything you need to determine why you are not being able to download and also explains how BitTorrent works, how to properly configure your client, how to open ports and so on.

---

### Post by fluffman86 on 2009-11-13
Yep, you're pretty much screwed.  Make sure the upnp is enabled in Transmission, on the off chance that it's enabled on the router as well.  You could also try talking to whoever is in charge of the router.  Maybe they can help you out.

---

### Post by ed-koala on 2009-11-13
Ignore this, the idea above about gufw and all else is excellent.

---

### Post by lovinglinux on 2009-11-13
I guess I wasn't fast enough when writing my previous post.

> **zookrider said:**
> Router fowarding is probably my issue.

I don't believe port forwarding is your problem. Most likely that you have conflicting firewall rules, as explained in my previous post, and that you are trying to download a torrent without enough peers or with the tracker down. There are some very popular trackers that are down since yesterday, so you won't be able to connect to any peers through them.

> **zookrider said:**
> I am in an environment where internet is being disseminated by a central router over which I have no control. Am I just screwed?

Most likely, but that depends on how the router is setup. For instance, if the router allows UPnP, then you are good. Nevertheless, as I explain in my tutorial, you don't actually need port forwarding from the router to download. It helps a lot to connect to more peers and thus get better speeds, but on a very popular swarm you probably will be able to get decent speeds without port forwarding. Nevertheless, that doesn't seems to be the case of the torrents you are trying to download.

---

### Post by zookrider on 2009-11-14
OK, I installed Deluge, and followed all other instructions in the Bittorrent guide, minus those having to do with the router because I have no access to it. I opened a new torrent in deluge and I got...nothing. Under status all fields are blank and I have a "No Incoming Connections!" warning at the bottom of the window. Sigh...

BTW, my connection is coming from a D-Link DES 1008d switch. Don't know if that's relevant.

---

### Post by lovinglinux on 2009-11-14
> **zookrider said:**
> OK, I installed Deluge, and followed all other instructions in the Bittorrent guide, minus those having to do with the router because I have no access to it. I opened a new torrent in deluge and I got...nothing. Under status all fields are blank and I have a "No Incoming Connections!" warning at the bottom of the window. Sigh...

Have you tried to download one of the recommended torrents like [Ubuntu ISO files](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)?

Also check the torrent details to see if the tracker is responding properly.

---

### Post by zookrider on 2009-11-14
> **lovinglinux said:**
> Have you tried to download one of the recommended torrents like [Ubuntu ISO files](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)?

Also check the torrent details to see if the tracker is responding properly.

Yes, same result. Tracker field is blank.

---

### Post by lovinglinux on 2009-11-14
> **zookrider said:**
> Yes, same result. Tracker field is blank.

You need to start the torrent then check if the tracker info show any error message.

---

### Post by mikewhatever on 2009-11-14
> **zookrider said:**
> Router fowarding is probably my issue. I am in an environment where internet is being disseminated by a central router over which I have no control. Am I just screwed?

Some networks don't allow bittorrent altogether, which may be your case, if you are on a school/organization's network, for example. There are several things to try in such cases, but bare in mind that you might be sidestepping the organization's networking policy with possibly negative consequences. Furthermore, we can't help you do that. ;)

---

### Post by siabost on 2009-11-14
Hi all,

I have a problem with Torrent downloads too:
Ubuntu 9.10 (only UFW loaded as per original installation - no rules set, in fact it might not even be enabled)
Transmission Bittorrent (tried Deluge also with same negative results).

I used to download successfully some time ago with Ubuntu 8.04 & Transmission via Rhythmbox/Jamendo i.e. via the button that triggers the Torrent. Though I didn't have an ADSL router then.

Trying it now with UPnP enabled, the Network & Web ports 51413/9091 open on the router I don't get any errors and the log reads as below:
```
Sat Nov 14 14:43:18 2009	     	RPC Server	Adding address to whitelist: 127.0.0.1
Sat Nov 14 14:43:18 2009	     	RPC Server	Serving RPC and Web requests on port 9091
Sat Nov 14 14:43:18 2009	     	RPC Server	Whitelist enabled
Sat Nov 14 14:43:18 2009	     		Transmission 1.75 (9117) started
Sat Nov 14 14:43:18 2009	     	DHT	Generating new id
Sat Nov 14 14:43:18 2009	     	Port Forwarding (NAT-PMP)	initnatpmp succeeded (0)
Sat Nov 14 14:43:18 2009	     	Port Forwarding (NAT-PMP)	sendpublicaddressrequest succeeded (2)
Sat Nov 14 14:43:18 2009	     	Afrika Freedom - dikobimouna -- Jamendo - OGG Vorbis q7 - 2009.09.02 [www.jamendo.com]	Couldn't read resume file
Sat Nov 14 14:43:20 2009	     	Port Forwarding (UPnP)	Found Internet Gateway Device "http://my-router-ip:49152/upnp/control/WANIPConnection"
Sat Nov 14 14:43:20 2009	     	Port Forwarding (UPnP)	Local Address is "my-computer-ip"
Sat Nov 14 14:43:20 2009	     	Port Forwarding (UPnP)	Port forwarding through "http://my-router-ip:49152/upnp/control/WANIPConnection", service "urn:schemas-upnp-org:service:WANIPConnection:1".  (local address: my-computer-ip:51413)
Sat Nov 14 14:43:20 2009	     	Port Forwarding (UPnP)	Port forwarding successful!
Sat Nov 14 14:43:20 2009	     	Port Forwarding	State changed from "Not forwarded" to "Forwarded"
Sat Nov 14 14:43:20 2009	     	Afrika Freedom - dikobimouna -- Jamendo - OGG Vorbis q7 - 2009.09.02 [www.jamendo.com]	Queued for verification
Sat Nov 14 14:43:20 2009	     	Afrika Freedom - dikobimouna -- Jamendo - OGG Vorbis q7 - 2009.09.02 [www.jamendo.com]	Verifying torrent
Sat Nov 14 14:43:25 2009	     		Using libcurl 7.19.5
Sat Nov 14 14:43:25 2009	     		Saved "/home/kenny/.config/transmission/settings.json"
Sat Nov 14 14:43:25 2009	     	Afrika Freedom - dikobimouna -- Jamendo - OGG Vorbis q7 - 2009.09.02 [www.jamendo.com]	Got 2 peers from tracker
```
It finds 2 peers as shown above and then just stops! A folder is created ready for the downloading of the file bu it never happens.

Could it be the tracker that is at fault? If it is, how can that be changed/fix?

I'm hoping this info will help me and everyone else here.

Many thanks.

---

### Post by lovinglinux on 2009-11-14
> **siabost said:**
> It finds 2 peers as shown above and then just stops! A folder is created ready for the downloading of the file bu it never happens.

Could it be the tracker that is at fault? If it is, how can that be changed/fix?

I'm hoping this info will help me and everyone else here.

Many thanks.

It's not the tracker, since the connection with it is established and it shows two connected peers. The problem is that the number of peers is too low.

---

### Post by siabost on 2009-11-14
Thanks lovinglinux,

Since posting I checked the properties of the torrent & both peers were "leechers" rather than "seeders".

So maybe it's simply there isn't anything to download?:(

Thanks

---

### Post by lovinglinux on 2009-11-14
> **siabost said:**
> Thanks lovinglinux,

Since posting I checked the properties of the torrent & both peers were "leechers" rather than "seeders".

So maybe it's simply there isn't anything to download?:(

Thanks

Yep, no seeders and only two peers means that torrent is pretty much dead.

---

### Post by prwnz on 2009-12-11
Hi Zookrider, I had the same problem after I tried to set up scheduling, tried everything to fix it. In the end it was increadibly simple, at the bottom left of the window there were two icons a gear and a rabbit, I clicked the rabbit and it popped up with 'Remove temp speed restrictions' and guess what... away it went.

---

### Post by jiex on 2009-12-11
Hello
I have a bittorrent issue that is confusing me. I use Ubuntu 9.10, with the latest upgrades, Ktorrent and the computer is connected thus:
Computer -> switch -> switch -> router -> cable modem.
The router is a Netgear   RP614v2. The Switches are Dlinks - all 1000mbs. 
I have a 2mbs connection.
All the other computers on the network (five of them) use XP; and I also have an Xstreamer and a beyonwiz also on the network, hence the switches. There is no wireless - all cabled, cat 5.
The issue is this. After a while, Ktorrent ceases to upload. If I try to download something, it comes up as "Stalled". If I reboot, then downloading commences immediately as does uploading. I am downloading UK TV programs from a private tracker.
Does anyone have any idea why it is doing this? 
It did not occur in a previous version of Ubuntu 9.x - but only started doing this after I went to 9.10.
Thanks for your help.

---

