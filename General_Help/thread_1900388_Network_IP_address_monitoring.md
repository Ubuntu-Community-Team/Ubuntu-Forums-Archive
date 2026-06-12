---
title: "Network IP address monitoring"
date: 2011-12-26
forum: General Help
---

### Post by gargoyle60 on 2011-12-26
I am looking for a tool that will dump information to a text logfile for Network IP address monitoring, generating text log entries similar to this...

  DoS udp_flood Block(10s) 212.69.36.3,53 -> 93.124.6.71,29705 PR udp len 20 399 ...

specifically "DoS" and "Block" entries. Then I can capture the soruce IP address, such as 212.69.36.3 in the above example. 

So far, those tools that I've looked at (iptraf, etherape) don't seem to generate this type/format of information as far as I can tell.

Can anyone recommend such a tool, if one exists?
Thanks

---
Ubuntu 11.10
Single user machine
Home network
3GB mem, 3GHz CPU

---

### Post by 2F4U on 2011-12-26
Did you already look at Wireshark?

---

### Post by The Cog on 2011-12-26
That's a log message from a firewall telling you that it's decided to block a certain type of packet for 10 seconds.

What are you trying to do, to achieve?

tcpdump will produce a packet log, but I really don't think you will be wanting to wade through a log of every packet into and out of your system.
> sudo tcpdump -i eth0 > tcpdump.txt

---

### Post by gargoyle60 on 2011-12-26
> **2F4U said:**
> Did you already look at Wireshark?

Interesting. I hadn't seen Wireshark. 

I've installed it but can only run as root despite following the instructions at [http://www.tavshed.com/?p=104](http://www.tavshed.com/?p=104) 
plus I can't see options for where it stores a continuous log file. 
But it looks useful so I shall persevere.

---

### Post by gargoyle60 on 2011-12-26
I see what you mean about tcpdump.
I am trying to capture/log all network traffic to/fom my machine via eth0, specifically those that my router marks as (potential) DoS attacks, whilst ignoring "regular" traffic from smtp/http/etc initiated by me, in other words I'm trying to log any attempts from external sources that might be attempting to penetrate my router's firewall (and which are hopefully blocked). 
The overall reason is so that I can monitor such attacks on an ongoing basis (I already do this under WinXP and wanted to do similar under Ubuntu))

---

### Post by The Cog on 2011-12-27
Hmm. The trouble is, when the firewall in the router decides they're DoS, it stops forwarding them to you (hence the Block(10S)). So nothing on your computer can log those - they don't arrive.

There is a utility called deny-hosts (I think) that runs on the PC and will selectively configure the inbuilt PC firewalling to drop the packets. This generates a log file, of course. I don't remember any more details, but if you look in the sticky posts at the top of the Security Discussions forum for a post by Bodhi.Zazen you will find lots of extremely good advice amd links there.

---

### Post by gargoyle60 on 2011-12-27
> **The Cog said:**
> Hmm. The trouble is, when the firewall in the router decides they're DoS, it stops forwarding them to you (hence the Block(10S)). So nothing on your computer can log those - they don't arrive.


Good point. 
I suppose I could concentrate on monitoring the other traffic, just in case something else suspicious gets through that my router doesn't have a rule for, such as other ports scans.

---

### Post by NadirPoint on 2011-12-27
I've found Snort to be useful for this type activity.

---

### Post by Synoc on 2011-12-27
Question for you:

Have you tried using the router to log that information and have it forward that log to you? that would be the only way to log all the information that gets "blocked" that I can think of. then then you can look through the file, and grep for any information you like, IP address, packet type, etc.

---

### Post by gargoyle60 on 2011-12-28
My router can log the information but as it's an older model it doesn't have forwarding facilities. In the past I've left an old Win98 machine running 24/7 and manually setting up a bespoke program to email me alerts periodically, but now I am wishing to completely ditch Windoze in favour of Ubuntu.

---

