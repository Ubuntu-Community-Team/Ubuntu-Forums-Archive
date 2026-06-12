---
title: "Cannot connect to torrent trackers or peers"
date: 2009-08-26
forum: General Help
---

### Post by rsfrost on 2009-08-26
Fairly new to Ubuntu but competent.

Two months ago I installed Ubuntu 9.04 on a old gateway laptop.  I've been primarily using it for web surfing, samba server and torrent downloading.  All had worked fine until a recent update using update manager on 08/23/2009.  I don't recall the specific updates addressed.

Since then I've had a problem with any torrent. It will not connect to the tracker or to any peers.  I will get a time out error on the tracker. I have successfully connected to other peers using the same torrent file on my Vista laptop connected to the same network.  This has occurred with multiple torrents.

Listed are the current steps I've gone through to resolve the issue without success.

1.  Verified and changed port forwarding on my router.  Torrent applications have verified that the port is open.
2.  I have Mobloquer peer blocking service installed.  I disable/stopped the service thinking a new list is blocking the connection.
3.  Disabled any peer blocking lists built into torrent apps
4.  I thought I might of had a firewall installed so I setup Firestarter to stop the service (none were running).
5.  I've purged and re-istalled my default torrent app Transmission.
6.  I've tried multiple other torrent applications

Nothing has resulted in any torrent application from connecting to the tracker.  At first I thought it was my ISP or router blocking the connection but I've confirmed that isn't the case as my Vista machine functions properly using the same ISP and router.

I'm at a loss and would rather not reinstall the OS as it took me a long time to get the system working the way it was until 8/23.  Any ideas?

---

### Post by nuketro0p3r on 2009-08-26
I am having the same problem. I am using ubuntu 8.04 LTS. I've also tried all of the steps mentioned above. The incoming ports used by the torrent clients are not blocked by my router. I've used Transmission, Deluge, rTorrent, KTorrent and BitTorrent Client but no use although I've just installed uTorrent with wine and I am getting around 35kbps which is around 4 to 5 times less of what I used to get in WinXp.

---

### Post by rsfrost on 2009-08-26
Thanks for he tip.  I've tried the same but no luck.  I guess I'll have to run the torrent on Vista until I can find a solution.

> **nuketro0p3r said:**
> I am having the same problem. I am using ubuntu 8.04 LTS. I've also tried all of the steps mentioned above. The incoming ports used by the torrent clients are not blocked by my router. I've used Transmission, Deluge, rTorrent, KTorrent and BitTorrent Client but no use although I've just installed uTorrent with wine and I am getting around 35kbps which is around 4 to 5 times less of what I used to get in WinXp.

---

### Post by rsfrost on 2009-09-17
I'll post a follow up on my original thread.  This issue has resolved itself either through a system update or luck.

A few days after posting this I went back to the issue to see if I could find any settings or files to reset or change but before I did I opened up a torrent and it connected to peers and started to download.

Again I'm not sure what caused it to stop working or then start again.  At the time there were issues going on with torrent trackers so I guessing that could have caused the issue but still seems strange my vista laptop didn't have the same problem.

---

### Post by Nilloc on 2009-09-24
nuketro0p3r i have actually done the same. i have gotten and ussed utorrent. but when i go to open containing folder it doesnt put me where the movie file is like it did in vista. i do use vlc. and i just want to know how to actually watch the movie once i have finneshed downloading it with utorrent. maybe you can help me.

---

### Post by Nilloc on 2009-09-24
sorry i figured it out. thanks though.

---

