---
title: "Internet speeds"
date: 2009-07-14
forum: General Help
---

### Post by Monotoko on 2009-07-14
Well, i was just on Windows XP, and getting speeds of 20kb/s, thought it was meant to be broadband!....it was a crippling experience. 

So i decided to reboot into Linux (Fedora to be exact) and tried to download the same file.....i was getting speeds of 200kb/s (at one point it reached 400!)

Also, whenever im downloading in Windows, its like my connection freezes, i cannot do anything else. Under linux when im downloading, its like it doesnt affect it.

So why is the internet so much faster on linux? Does it optimize my wireless card better? Do my ISP give Linux machines priority because there are more linux servers or what?

---

### Post by lukeiamyourfather on 2009-07-14
It could've been related to the wireless drivers or configuration in Windows, or a virus in Windows. Generally the ISP doesn't care what operating system is used. Cheers!

---

### Post by Brandon Williams on 2009-07-14
The TCP tuning in Linux is better for broadband than the tuning in Windows XP. The Windows config should be good enough for most people to 3+ Mbps though, so I doubt that's it. Still, Ubuntu with it's default parameters will be able to sustain higher internet throughput than XP with it's default parameters.

---

### Post by lukeiamyourfather on 2009-07-14
> **Brandon Williams said:**
> The TCP tuning in Linux is better for broadband than the tuning in Windows XP.

True, but not enough to account for an order of magnitude difference in throughput. Something was funky in Windows if it was running that much slower.

---

### Post by doas777 on 2009-07-14
I'm glad your getting better bandwidth.

always be careful to check the case of the 'b' in kb. kb => kilobits, kB => kilobytes. 
XP on my gigabit network runs at the same speed as the ubuntu boxes. amusingly enough, since intel has a bug in the e1000 drivers, i can't even get gigabit on most of the intel cards in my house, except by using xp. 

don't get me wrong, I don't prefer XP, but if that is the max you were getting, then somthing was wrong with  your box (most likely software if ubuntu runs it fine). that is not typical of the os. also i usually find that the speed limitation on the internet is not a problem with my hardware, but my ISPs and the server I'm connecting to's. not much I can do about it except optimize my router.

cheers

---

### Post by Brandon Williams on 2009-07-14
> **lukeiamyourfather said:**
> True, but not enough to account for an order of magnitude difference in throughput. Something was funky in Windows if it was running that much slower.

Actually, it could account for an order of magnitude difference, especially if you have horrendous latency. However, if the real throughput is 20KBps (160Kbps), that can only be accounted for with the Windows XP default parameters (no window scaling) if the round trip time is longer than 3 seconds, which is not very likely.

That said, with a more reasonable RTT of 200msec, the XP defaults would limit you to about 2.6Mbps (300kbps), while the Ubuntu defaults would be high enough to allow you to use the full bandwidth provided by your ISP. That would only mean 2x or 3x improvement for most people, but it could mean much more than that.

On a LAN, none of this would matter because the RTT on a LAN would be so short that the absence of Window scaling would not be a limiting factor. It also wouldn't be an issue with Windows Vista, where scaling is on by default.

---

