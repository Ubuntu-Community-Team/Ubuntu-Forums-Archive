---
title: "Extremely slow network speeds"
date: 2011-01-06
forum: General Help
---

### Post by brc3 on 2011-01-06
Hi all,

I'm on Lucid and having the craziest problem with my internet connectivity. Actually it's the network speed in general. Here's the problem:

I am using bbtether most of the time, which works fine for the first few minutes. However, anywhere from five web pages to twenty youtube videos later my network speed slows to a near halt. When trying to download a file, chromium shows an initial download speed of around 3 MB/s (yes, megabytes). It will download for a few seconds and then drop to a ridiculous < 1 KB/s rate. I know that my phone can handle up to a 3 Mbps transfer speed, but these rates are absurd. Even when I try downloading something from the Ubuntu repository, it will download for around 30 KB/s for a bit, then jump to like 700 KB/s, then stop altogether. 

At first I thought it might be the chat script for bbtether, but it does the same thing whether the modem speed is set to 115200, 230400, 460800 or 921600. After taking my laptop to school I found that I am having the same problems on both a wired AND wireless connection. The connection at school is around 65 Mbps (so says the network manager), but the download process still goes the same: starts off extremely fast then drops to a crawl within seconds, although I seem to be able to browse the web for a while longer than with tethering. I have tried downloading large files from several different sites and I always get the same results.

Now here's the kicker: regardless of whether i'm on a wired, wireless, or tethered connection, every time it happens I can just disconnect, and then reconnect, and speeds are fine again for a few minutes. But without fail it will always slow down to a halt again... The really weird thing is that sometimes my connection will be fine for an hour or two, and then on the very next connection i'll only get 5 minutes of good speeds. 

I know it's not my web browser because it happens in both firefox and chromium, and when i try an apt-get install through the terminal it also does the same thing. I have checked the memory and processes and found nothing out of the ordinary. Also disabled IPv6 and tried disabling all the other network interfaces not being used but no luck.. All my hardware is compatible with Linux so i'm pretty sure there are no driver issues. 

I would greatly appreciate any help I can get on this one,

Thanks

---

