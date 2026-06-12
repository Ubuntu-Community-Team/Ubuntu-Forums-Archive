---
title: "Switching between torrent clients with active torrents?"
date: 2009-07-15
forum: General Help
---

### Post by Nixie Pixel on 2009-07-15
Hi, I am in the middle of a 50-GB torrent download and have finally gotten fed up for the last time with Vuze's behavior (download patch, indicate it has to reboot, reboot, download same patch again, rinse, repeat...).

Unfortunately I'm a good ways into this download, which is taking forever, and I don't want to lose the data I have already received. How can I pull this active download into Transmission (or another client, if there is a better one out there) and have it pick up where Vuze left off?

Alternately, if there is a way to stop Vuze from doing the patch-reboot-patch process, I would love to hear it, but I have searched and searched for how to stop it, and can't find any info.

Thanks!

---

### Post by TeoBigusGeekus on 2009-07-15
Install Ktorrent and then go to File-> Import Torrent.
If all goes well you can uninstall Vuze.

---

### Post by michy99 on 2009-07-15
In whatever client you use, when you start the torrent, point it at the directory where the partial file is located and it should continue from there.

---

### Post by jerome1232 on 2009-07-15
> **michy99 said:**
> In whatever client you use, when you start the torrent, point it at the directory where the partial file is located and it should continue from there.

Just what I was about to say, I just assumed this was the case and tested it out before I posted lol.

---

### Post by hibliss on 2009-07-15
I personally would choose Deluge or ktorrent over Transmission, due to Transmission stalling on some trackers for no apparent reason.

---

### Post by t4thfavor on 2009-07-15
I agree with above just point Transmission to the location of the partial file, and start the torrents. I did that when I move off utorrent/wine to Transmission.

I maybe noticed the stall on some trackers, but I have yet to have a torrent not finish due to it.

---

### Post by hibliss on 2009-07-15
> **t4thfavor said:**
> I maybe noticed the stall on some trackers, but I have yet to have a torrent not finish due to it.

For me, any stalling is not acceptable if the client is properly configured. ktorrent and rtorrent start the same torrent within seconds, why doe sit take Transmission 15 minutes or more sometimes?

---

### Post by t4thfavor on 2009-07-15
Like I said, I can't be for sure that it stalls, it's never noticable if it does, and I have never missed a torrent on account of any wierdness with Transmission.

---

### Post by Nixie Pixel on 2009-07-15
Thanks, I pointed Transmission to the torrent file in /.azureus/torrents/ and the download the the torrent download in /Azureus Downloads/, but it didn't pick up where Vuze left off. Any ideas what I did wrong? Should I point the download directly to /Azureus Downloads/?

---

### Post by t4thfavor on 2009-07-15
Check where you told Transmission to download too, its adjustable per torrent so make sure you have it set when you "add" the torrent.

---

### Post by Nixie Pixel on 2009-07-15
Ok, yeah, that was the answer, I just had to point it to Azureus Downloads rather than the specific download directory - it found my currently downloaded bits and picked up where it left off!

Thanks!

---

### Post by t4thfavor on 2009-07-15
Knew it wouldn't be that hard!

---

