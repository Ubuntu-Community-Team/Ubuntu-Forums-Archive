---
title: "Lucid Lynx freezes while using bittorrent"
date: 2010-08-08
forum: General Help
---

### Post by Yleeyas on 2010-08-08
Before I describe my problem let me say that I've searched this, and other linux forums to no avail. I'm on page 50 of the 80+ page opus thread on 'random freezes' by lkrory21, and none of the many freeze scenarios resemble mine, though I have attempted some of the solutions without success.
I've searched launchpad bugs and answers; no joy.
I've searched bittorrent applications forums without success.

So here goes:

I did a clean install of Ubuntu 10.04.1 (overwriting a dual boot Ubuntu 8.04/XP system) on my Compaq Pressario 6410. The system runs perfectly except when I use Transmission bittorrent app. (I tested Deluge and get the same problem)

After some arbitrary time interval, anywhere from half hour to 6 hours after the start of the torrent(s), and I've gone to bed, the system 'freezes' as indicated by:

- system clock in top panel stopped ticking
- two system monitor graphs in the top panel are nolonger updating
- the transmission window is frozen with some arbitrary throughput/connections numbers
- system logs have not updated since the freeze, and there are no entries reflecting problems of any kind that I can see-
- same with the transmission log

Here's the kicker, unlike most of the other freeze problems, I don't require a reboot.
All I have to do is wiggle the mouse and everything starts moving again: 

- system clock starts ticking again, but from the time it stopped, which is nolonger the correct time
- note that the hardware clock is unaffected and I use 'sudo hwclock -s' to reset the system clock to the correct time
- the system monitor graphics start updating again
- the transmission window shows that all the links have been dropped, but it starts reconnecting and the transfers startup again.
- system logs start being written again as if nothing happened, (with the newly set correct time).

Here's some of the things I've tried, without success:
- replaced CMOS battery (early in the game I thought is was just a clock problem)
- tried Deluge (as mentioned) but same problem
- ran gconf-cleaner
- disabled DHT on bittorrent client, and throttled throughput and connections configuration on bittorrent (got this from transmission forum)
- no special effects (compiz,etc)
- disabled screensavers and power management

This is a most annoying problem, certainly not as bad as most of the other freezes I've been reading about, but still, most annoying. I'm hoping it's something obvious and dumb that I'm overlooking.

Any insight into what's happening, and possible solutions, would be much appreciated.

---

