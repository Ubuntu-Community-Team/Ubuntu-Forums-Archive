---
title: "torrent client speed comparison (too slow)"
date: 2009-11-05
forum: General Help
---

### Post by ticktricktrack on 2009-11-05
I've used the same .torrent file and the same settings to compare a few torrent client. This file had a seed:peer ratio of 5:1, over 5000 seeds and might or might not have been semi-legal.
Conclusion: All clients on Ubuntu they are terribly slow. It sometimes is a little bit annoying that I have to switch to windows to download a couple GBs of stuff.

On all 4 tests: 
-same settings
-ports were open
-same torrent
-same time (10 mins apart)
-same connection 30mbit down / 2mbit up
-same PC


Transmission:
After 1 min:  39 kb/s
After 10 min: 70 kb/s

Vuze: 
After 1 min:  64 kb/s
After 10 min: 191 kb/s

Deluge: 
After 1 min:  200 kb/s
After 10 min: 600 kb/s

**And the winner is:**
[COLOR="DarkRed"]**uTorrent on Windows XP**[/COLOR]
After 1 min:  400 kb/s
After 10 min a whopping: 2300 kb/s

---

### Post by AteZ on 2009-11-05
have you tested your network speed with other applications?
i had the same results on a laptop and it was slow due the suboptimal driver for broadcom wifi cards.

---

### Post by ticktricktrack on 2009-11-05
Did a DSL test online:
Down: 33.165 kbit/s (4.146 kByte/s)
Up: 1.980 kbit/s (248 kByte/s)

A quick test with an Ubuntu image from a nearby university confirms that.

---

### Post by wildweathel on 2009-11-05
You missed rtorrent.  It's ugly by modern standards (gotta love the ncurses console interface...), but it's specifically designed for efficiency.  Assuming 1) you don't have a problem with your network-adapter's driver and b) that variation isn't due to luck, it should be faster than any of those and use less memory.

That said, the difference between different clients shouldn't be that big.  How did you come up with those numbers?  Did you just copy down the reported instantaneous speed after 10 minutes?  What order did you test them in? Bittorrent is very variable; I wouldn't draw any conclusions from less than an average over a couple-hundred MB.

---

### Post by lovinglinux on 2009-11-05
> **wildweathel said:**
> You missed rtorrent.  It's ugly by modern standards (gotta love the ncurses console interface...), but it's specifically designed for efficiency.  Assuming 1) you don't have a problem with your network-adapter's driver and b) that variation isn't due to luck, it should be faster than any of those and use less memory

There is also KTorrent, which is my choice for KDE, like Deluge is my choice for  Gnome.

> **wildweathel said:**
> That said, the difference between different clients shouldn't be that big.  How did you come up with those numbers?  Did you just copy down the reported instantaneous speed after 10 minutes?  What order did you test them in? Bittorrent is very variable; I wouldn't draw any conclusions from less than an average over a couple-hundred MB.

I agree. Besides every client has it's own tricks. For example in Deluge I connect to a lot of peers as soon as I start a torrent with a decent ratio, but in KTorrent I connect only to a few dozens. I don't know if this is due to the fact that I have been improving my blocklists since I started to use KTorrent. Nevertheless, I discovered that if you manually announce to the tracker when the number of peers stabilizes, you get more peers and better speeds. So I do a couple of manual announces on new torrents, then just relax.

Now, some questions about your test:

What exactly were the identical settings between clients?

Did you use DHT on all of them?

Did you use forced encrypted connections or not on all of them?

Did you change your IP after testing each client? If not, then the last client tested will probably get more incoming connection requests, because, between the first test and the last one, more peers would have scraped the tracker and received your IP as a potential peer.This would ultimately result in better speeds in the short period of time in which you have tested the clients. What was the order of clients tested?

---

### Post by NFblaze on 2009-11-05
It's pretty dificult to test the speed of clients, because everything is based off of the uploaders and how much they are uploading to you (which can vary), also, the availability of different pieces at different times can also affect the results.

---

### Post by ticktricktrack on 2009-11-06
my settings were:

downspeed max: 0kb
downspeed per torrent: 0kb

upspeed: 40kb total (high enough to not get throttled, low enough to avoid choking)
upload slots: 4

DHT: yes if present
encryption: forced

I monitored the speeds all the time and after 10 Minutes I recorded the minute average (estimated by brain) speed if it wasn't a peak. utorrent achieved >3MB/s for a few seconds, I didn't take that number.

> Did you change your IP after testing each client? If not, then the last client tested will probably get more incoming connection requests, because, between the first test and the last one, more peers would have scraped the tracker and received your IP as a potential peer.This would ultimately result in better speeds in the short period of time in which you have tested the clients. What was the order of clients tested?

To be honest, I didn't do this scientifically. Mainly because this isn't really a one time experience. I just wrote down number this time, out of boredom and annoyance. Deluge and uTorrent seem to be very similar in features and Deluge works fine and sometimes it reaches my connection maximum as well. But it just isn't as reliable to push the speeds to the maximum, as uTorrent is.

---

### Post by muhannadfa on 2009-11-06
@ ticktricktrack: actually man u're totally right, this is not utorrent or software problem
its being windows or ubuntu, u can use vuze on ubuntu & see the diffirence 
i used and tried many thing on ubuntu to overcome this annoying thing and it didn't work
& for the record nothing is being scientific here, so don't bother what r they saying

---

### Post by P4man on 2009-11-06
Your tests would be more interesting if you changed a few things.
First of all, use a legal and known uber fast torrent, like one that seeds ubuntu. Try this one:
[http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent)

Having a torrent with 5000 seeders is good but if 4500 of them have capped their upload to 5 kb/s you will still get hugely varying results depending what seeders you happen to connect to.

Next, you dont mention your connection and network settings. Have you at least made sure port forwarding is set up correctly? Different clients use different default ports, some use random ports (and some ISPs throttle certain ports). Use the same ports on all clients and test the port forwarding.

Then make sure you have comparable settings for stuff like number of connections. At least I assume you verified you didnt have bandwidth throttling enabled on any of the clients?

I have no problems maxing out my connection with any bt client on either windows or ubuntu, but if you get different results with the above changes Id be interested in learning.

BTW are you using wireless internet connection?

---

### Post by ticktricktrack on 2009-11-06
Wow, I just thought I put my experiences with torrent clients in here, but it seems I have to do a proper scientific study to make my point. With labcoats and [Kari from Mythbusters]("http://media.ebaumsworld.com/mediaFiles/picture/234619/1062722.jpg") and all that.

Well to clear things up: 
**I still am a user, which means I don't want to configure stuff, instead it should work out of the box. (more or less)**

**I won't use legal and uber fast torrents**, because I can direct download those and more importantly: **I download what I actually want to watch or listen to!**

---

### Post by P4man on 2009-11-06
> **ticktricktrack said:**
> 

Well to clear things up: 
**I still am a user, which means I don't want to configure stuff, instead it should work out of the box. (more or less)**

Fine but then you are drawing wrong conclusions. All you can say is that on *your* machine with *your* router and settings and *your ISP* using your wired or wireless connection it seems that ubuntu  clients are not as suitable to download **illegal torrents**. And perhaps even that is only true if you are too lazy to set your network settings properly in the clients.

thats a different conclusions as " Conclusion: All clients on Ubuntu they are terribly slow. "

FWIW using illegal torrents its entirely possible your bt client is being blocked by seeders. But if you dont even want to test a legal torrent, you'll never know.


edit: you didnt reply if you were using **wired** or **wireless** connection. Bittorrent is extremely stressfull on (wireless) network connections and you might have issues with you wifi driver . Then again if you dont want to solve a problem but just rant, then be my guest. You may want to post in community cafe instead of general help though.

---

### Post by NickJones on 2009-11-06
uTorrent works under Wine. And I find my typical HTTP browsing to be so much faster under Linux.

---

### Post by lovinglinux on 2009-11-06
> **ticktricktrack said:**
> Wow, I just thought I put my experiences with torrent clients in here, but it seems I have to do a proper scientific study to make my point. With labcoats and [Kari from Mythbusters]("http://media.ebaumsworld.com/mediaFiles/picture/234619/1062722.jpg") and all that.

You are being contested because your post suggest a scientific method backing up your conclusions. You didn't post your opinion, but test results conducted using controlled variables, that are are intended to provide a reliable set of data. When you do that, you must be prepared to be contested. That's how scientists work. 

Unfortunately, your method is completely flawed. You didn't use the same variables on all the tests (DHT just when available, half-open connections and connections per minute not controlled and so on) , you didn't make sure the tests weren't cross-contaminated (didn't change your IP between tests and make sure all established connections were terminated between tests), you didn't use enough data samples and a time frame that would mitigate anomalies and expected variations.

> **ticktricktrack said:**
> Well to clear things up: 
**I still am a user, which means I don't want to configure stuff, instead it should work out of the box. (more or less)**

They work out-of-the-box in Ubuntu. Nevertheless, getting maximum speeds with BitTorrent is not that simple. For instance, Windows users need to bypass the half-open connection limits imposed by the OS to achieve optimal results.

So, if you didn't test the torrent clients with a clean install of Ubuntu and Windows, without changing any OS settings, then the "out-of-the-box" condition is not valid for comparison.

> **ticktricktrack said:**
> **I won't use legal and uber fast torrents**, because I can direct download those and more importantly: **I download what I actually want to watch or listen to!**

If you want to provide results based on a controlled method then you need to reduce the possible variables and anomalies. That's why other users are suggesting using an reliable torrent, like from Ubuntu releases. Besides, promoting, discussing or linking to illegal downloads is not allowed in these forums.

> **ticktricktrack said:**
> To be honest, I didn't do this scientifically. Mainly because this isn't really a one time experience. I just wrote down number this time, out of boredom and annoyance. Deluge and uTorrent seem to be very similar in features and Deluge works fine and sometimes it reaches my connection maximum as well. But it just isn't as reliable to push the speeds to the maximum, as uTorrent is.

You actually did the test scientifically, but your method was flawed. 

I'm sorry if all the questions and comments upset you, but as far as I can see no one has overreacted or posted impolite comments. We are just trying to establish the reliability of the tests, because we do not perceive, in real-life conditions, the differences you are claiming on your thread title and experiment. Besides, like they say on those tribunal TV shows...."you opened the door counselor".

---

### Post by wildweathel on 2009-11-06
ticktricktrack,

I don't feel like being an accessory to your copyright infringement.  Nor am I willing to work with someone who wants his system to *be optimized*, but won't put in the effort to *optimize* it ([which starts with measuring performance]("http://catb.org/%7Eesr/writings/taoup/html/ch12s02.html")).  I'll help people solve problems, but I can't fix stuff for them, so I'm leaving this thread.

You didn't pay for the OS.  You don't pay for the content.  But, most people will ask you pay for tech support by being open-minded, objective, and diligent.  

Have you considered that BitTorrent might be about making use of your otherwise-idle uplink rather than being a tool for *getting* reruns of The Office?  Or that help forums might be more about cooperation than *getting* help.  Strive to [*put*]("http://catb.org/%7Eesr/writings/cathedral-bazaar/homesteading/ar01s06.html"), even if the only thing you can contribute is a [good question]("http://www.catb.org/%7Eesr/faqs/smart-questions.html#intro").

I'm sorry to hurt your feelings.  However, I fear if I don't say anything, you won't realize why people ignore you.  May you have better luck in your other endeavors.

---

### Post by sloggerkhan on 2009-11-06
I use a deluge on a variety of trackers and on anything well seeded, I can max out my entire download bandwidth to the point that using the internet for anything else is pretty much an impossibility. If I can't it's usually do to restrictions on the tracker, or garbage peers.

---

