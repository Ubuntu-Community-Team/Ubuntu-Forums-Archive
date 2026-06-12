---
title: "Why does my network usage look like this (see screenshot)"
date: 2010-06-24
forum: General Help
---

### Post by blur xc on 2010-06-24
I first noticed it doing this way back on 9.04, but now I've done a clean install of 10.04 and it's still there.  It looks like this on a fresh boot with no applications open.

How do I see what programs and transferring the data, and is there a way to see what is being transfered?

Thanks,
BM

---

### Post by CharlesA on 2010-06-24
It's just idle traffic. Probably arp requests and junk. If you really want to see what is being sent, use something like Wireshark or tcpdump. I don't know if there is any way to see what is sending data outside of just capturing the packets.

I just checked my Ubuntu VM and it's sitting at 0bytes sent/received, but it's isolated on the network.

---

### Post by blur xc on 2010-06-24
My Ubuntu VM (on my Windows computer) shows zero network usage when it's sitting idle.  It's on a wired lan, maybe that's the difference.

That seems like a lot of traffic for just idle usage.  I can recall way back when I first started using Ubuntu and had set up my conky to show my up/down speeds, it didn't' show nearly this much at idle.  I'm also wondering because my root partition is slowly growing.  A week ago it was at 4.8gb, now it's 5.2, and I haven't installed that much new software since then.

Thanks,
BM

---

### Post by CharlesA on 2010-06-24
The size growth might be due to updates. Have you run an apt-get autoclean/autoremove to see if the free space increases?

---

### Post by blur xc on 2010-06-24
> **CharlesA said:**
> The size growth might be due to updates. Have you run an apt-get autoclean/autoremove to see if the free space increases?


Nope- haven't gotten that far.  I'll give it a whirl and see how it goes...

The thing is, I do updates weekly, but I see my hdd usage incrementally rising day in and day out...  If there's data transferring between my pc and the outside world, where is it being stored?  

BM

---

### Post by CharlesA on 2010-06-24
Very strange indeed. Maybe try running du --max-depth=1 -h /

---

### Post by blur xc on 2010-08-19
Figured it out - [nethogs]("http://www.ubuntugeek.com/nethogs-net-top-tool-grouping-bandwidth-per-process.html") is the hot ticket.  It's pidgin for crying out lout.  I guess it's pinging the servers checking on the status of my contacts.  I killed all instances of pidgin, closed FF, etc, and it quieted way down.  There was the occasional blip of traffic, but for the most part, it all went away...

So yeah- it's a good feeling knowing what the heck is going on with my system...

Thanks,
BM

---

