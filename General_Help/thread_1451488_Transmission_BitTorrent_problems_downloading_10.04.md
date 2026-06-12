---
title: "Transmission BitTorrent problems downloading 10.04 beta2"
date: 2010-04-10
forum: General Help
---

### Post by DawieS on 2010-04-10
Previously, I have downloaded Ubuntu distro's directly with http. Last night I was seeding 3 completed torrents downloaded with Transmission BitTorrent, and decided to download the Ubuntu 10.4 beta2 version via torrent. I downloaded the torrent from the official Ubuntu website, and started the torrent at 23h35. I watched it set off at 35 KB/s, downloading from 50 of 60 connected peers, with a projected completion time of 6 hours, before going to bed.

This morning I was expecting the torrent to be finished downloading, and busy with seeding. I was surprised to see that it was only 20% completed, with a projected completion time of 5 hours. It has downloaded 895 MB, of which it only 'had' 141 MB, and uploaded only 3.8 MB, while the other 3 torrents have progressed well towards the uploading target ratio. I then paused and stopped the torrents, planning to investigate the problem later.

Attached please find a screen-shot of the properties tab of the torrent I took this morning. Also please note that the running time was 8 hours according to the logs, and not 4 hours as reported on the properties tab.

I have just restarted the torrent, and watched it for a while, this time leaving the other torrents paused. I left the Properties tab open, and could see the increasing numbers 'Downloaded' versus 'Have' increase by a factor of about 6 to 1. This implies that that I will consume about 4.2 GB of bandwidth, and take more than 2 days, to complete this torrent.

I never had any problems with other torrents using Transmission BitTorrent. I have noticed that torrents consume slightly more bandwidth compared to direct downloads, due to the extra overheads involved. However, a factor of 6 is definitely outrageous.

Additional info: I am using Ubuntu 9.10 32 bit desktop version. I do port forwarding on the router, and have a fixed IP on the LAN side of the router. I have a 384 kb/s ADSL line, with 40 KB/s down-, and 12 KB/s upload speed. I have updated the block-list of Transmission, and use Firestarter as a firewall interface. I have not seen any abnormalities in the active connections, or system log files.

Have anyone came across something similar before? Is there perhaps something wrong with the torrent, or perhaps the tracker? Any advice would be much appreciated.:smile:

---

### Post by ron999 on 2010-04-10
Hi
If you're serious about downloading the Ubuntu file then, imo, you should have had those other torrents paused all the time. Then re-start them when you've got the Ubuntu file.

Right now I think you ought to right-click the Ubuntu torrent and 'Verify Local Data'.

---

### Post by DawieS on 2010-04-10
I have just tested with the other uploading torrents paused or active. It does not make any difference in the downloading torrent. It seems as if there is a 6 fold duplication in the data downloaded for this torrent.

I have verified the data downloaded, and it verifies only about 150 Mb. I don't know what the rest is, must be duplicates and a bit of overheads?

---

### Post by DawieS on 2010-05-01
Update:

I eventually gave up on downloading with Transmission and used http to download the beta version, that I have since updated and customized.

However, some family and friends asked me to burn them some CD's when the official version of Lucid is released. To avoid traffic congestion on the servers, I again fetched the torrent file and started downloading with Transmission, after updating the block-list. I kept an eye on the torrent for about 2 hours, and saw that it was running perfectly normal. It had verified about 220 MB of the total of 250 MB downloaded, when  I went to bed.

When I got up the next morning, it had verified 240 MB (progressed only 20 MB) and downloaded more than 950 MB, of which it reported only 2 MB as being corrupted. I then came to the conclusion that I was being spammed.

So it seems as if we have some real enemies out there! Those people have nothing better to do other that borking other people's downloads! What a waste of bandwidth!

Obviously I would appreciate the opportunity to get into physical contact with these people. Any ideas on how to get hold of them?

---

### Post by jenks on 2010-05-04
I just tried downloading both the desktop and alternate i386 versions of 10.4 using the torrent links on ubuntu.com using the transmission on my up-to-date Karmic. I consistently get the error "Couldn't add corrupt torrent" for both torrents, whether I launch transmission from the browser or try to open the downloaded torrent files from transmission. I also seem to have something called BitTorrent Download Client installed, so I tried that and it also claimed that the torrent files are "bad".

I suppose I can install more torrent clients and keep trying. I am totally amazed to see this happening, after telling friends just this morning how polished Ubuntu has become, but what really puzzles me is that I couldn't find another single post about this issue. Is it really that sudden a problem, or is my system somehow different than everyone else's? Admittedly I am behind a firewall that blocks some sites, but I don't see how that would consistently corrupt torrent files. I hope this isn't widespread.

P.S. I just tried an ubuntu torrent from Santa Barbara's mirror with the same result.

---

### Post by DawieS on 2010-05-06
Update:

I was using the default BitTorrent client in Karmic (Transmission 1.91 (10264)) with my previous two aborted attempts downloading the Lucid beta2 and final release versions. The block-list contained 88870 rules during the torrent run (now has 92858 rules after a recent update).

After installing Lucid beta2 downloaded and updated via http, I noticed that the default BitTorrent client in Lucid (Transmission 1.92 (10363)) contained 224559 rules in the block-list. Since I still needed the final release CD, I decided to give it one more try downloading by torrent, this time in Lucid.

I downloaded a fresh torrent file from the Ubuntu website and started downloading. This time the torrent run was successful, downloading  a total of 743 MB for the verified size of 698 MB. The 'wastage' thus was 6%, which is a great improvement on the +580% of the previously aborted torrents using Karmic.:razz:
:razz::razz:
I also noticed that the torrent only started seeding after being completely downloaded and verified, whereas in Karmic, it was also seeding while downloading. The newer version also had a much stricter control on the closing of ports, and closed all ports soon after being used, whereas in Karmic I was always left with a list of hanging open connections after a torrent run.

For me this experience was a 'catch 22' situation (I must first have Lucid before being able to successfully download Lucid via torrent).

> **jenks said:**
> I just tried downloading both the desktop and alternate i386 versions of 10.4 using the torrent links on ubuntu.com using the transmission on my up-to-date Karmic. I consistently get the error "Couldn't add corrupt torrent" for both torrents, whether I launch transmission from the browser or try to open the downloaded torrent files from transmission. I also seem to have something called BitTorrent Download Client installed, so I tried that and it also claimed that the torrent files are "bad".

I suppose I can install more torrent clients and keep trying. I am totally amazed to see this happening, after telling friends just this morning how polished Ubuntu has become, but what really puzzles me is that I couldn't find another single post about this issue. Is it really that sudden a problem, or is my system somehow different than everyone else's? Admittedly I am behind a firewall that blocks some sites, but I don't see how that would consistently corrupt torrent files. I hope this isn't widespread.

P.S. I just tried an ubuntu torrent from Santa Barbara's mirror with the same result.
I don't think that you will be able to run torrents from within most of the 'corporate type' networks, unless you are able to connect via an external proxy. They will just not allow it, with the reason that their network is not capable of handling the additional strain caused by the large number of concurrent connections done by torrents.

If you are running from your own 'home type' LAN behind your own modem/router firewall, you will find that torrents usually run better if you do port forwarding. To see how to port forward on your specific modem/router, please visit [http://portforward.com](http://portforward.com).

If you also run a firewall on your PC, you should adjust the inbound traffic policy on the firewall, to allow traffic to get through to BitTorrent.

If you still have problems running torrents, please start a new thread (I will mark this one as solved).

---

