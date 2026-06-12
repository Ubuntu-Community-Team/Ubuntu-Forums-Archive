---
title: "Transmission does not limit download speed"
date: 2009-10-15
forum: General Help
---

### Post by akudewan on 2009-10-15
I have a 256kbps internet connection. I need to throttle my torrent download speeds very often, so that I can browse simultaneously.

Transmission has a speed-limit feature, I had set the d/l speed to 15kBps. However, this feature appears to be a joke. It simply shows my 15kBps in the main window while it is actually downloading at 30-32kBps.

[[IMG]http://imgur.com/GMBoVs.png[/IMG]](http://imgur.com/GMBoV.png)

I'm using version "Transmission 1.51 (7963)"
Has anyone else faced this problem? Is there a solution to this? Should I file a bug report?

(Edit: I also tried Deluge. It also lies about the download speed, the throttling doesn't work)

---

### Post by P4man on 2009-10-15
It works fine in deluge for me. What you are seeing in the panel, is that a network manager? If so, its probably another app that is using your bandwidth. try pauzing transmission and see if it drops to zero or not. I throttle my torrents all the time, and while it takes a bit for it to adjust, it works a treat (with deluge at least).

---

### Post by Giblet5 on 2009-10-15
Maybe the "15Kbps" setting is full duplex (15k up, 15k down, 30k total)?

It makes sense.

Torrent is bi-directional.

Someone setting 15Kbps would be more annoyed that their download occurs at 7.5Kbps... Programmers and UI designers have to make trade-offs because the average user is dumber than a bag of hammers.

Anyone checking the actual bandwidth allocation is smarter and therefore limited to two or three people. :)

---

### Post by justleen on 2009-10-15
I found that I need to change it in the preferences for it to work. Right click on a torrent, and then setting a speed limit does not seem to work.

---

### Post by akudewan on 2009-10-15
> **P4man said:**
> It works fine in deluge for me. What you are seeing in the panel, is that a network manager? If so, its probably another app that is using your bandwidth. try pauzing transmission and see if it drops to zero or not. I throttle my torrents all the time, and while it takes a bit for it to adjust, it works a treat (with deluge at least).

Yes, thats a network manager (netspeed-applet). There were no other processes using the net at the time. Pausing the torrent did make the speed in all monitors drop to zero.

When I limit the download speed to 5kBps in Transmission, it gives me a *real* speed of ~15kBps. Thats what I really want...

---

### Post by akudewan on 2009-10-15
> **justleen said:**
> I found that I need to change it in the preferences for it to work. Right click on a torrent, and then setting a speed limit does not seem to work.

I tried both ways. It gives me the same result in both cases.

---

### Post by P4man on 2009-10-15
For the record, to not interfere with your browsing, you should limit your *upload* mostly. Ironically. If your upload is maxed out, as bittorrent does easily, browsing becomes terribly slow, even though browsing is a download mostly. thats because of how TCP works, every packet has to be acknowledged (which is small, but upload) and if you upload bandwith is already maxed, then it will take forever just to view a webpage.

Your download you can keep pretty close to your maximum bandwidth, and you will probably hardly notice.

---

### Post by donato roque on 2009-10-15
p4man is right, do not limit your download traffic, to achieve the effect you want set limits to your upload speed.  The exact number is really a matter of trial and error.  What you can do is measure your upload speed then set you upload limit to about 70% and adjust according to your preferences.

---

### Post by akudewan on 2009-10-15
Thanks for all the responses. After some playing around, I have noticed that the speed limit does kick in after 2-3 minutes. It keeps fluctuating wildly, but seems to average out to the limit specified. ([Possible explanation here]("http://forum.transmissionbt.com/viewtopic.php?f=1&t=7159")).

I can live it for the time being. Thanks everyone!

---

### Post by Charles Kerr on 2009-10-15
The speed limit monitor -- as well as the options for limiting individual torrents vs global limits and off-hour speed limits -- has changed between Transmission 1.5x and 1.75.  You might want to give the newer version a spin in Karmic.

---

